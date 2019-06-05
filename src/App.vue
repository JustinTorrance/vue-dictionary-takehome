<template>
  <div id="app">
    <div class="app-container">
      <h1 class="title">Thesaurus Park</h1>
      <Search v-on:handle-click="handleClick" />
      <h3 class="synonyms-for" >Synonyms for: {{ searchedWord }}</h3>
      <SynonymsContainer v-bind:synonyms="synonyms" v-on:handle-click="handleClick" />
      <h3 v-if="emptyReturn">Sorry, there are no synonyms for this word</h3>
    </div>
  </div>
</template>


<script>
  import Search from './components/Search'
  import SynonymsContainer from './components/SynonymsContainer'

  export default {
    name: 'app',
    components: {
      Search,
      SynonymsContainer
    },
    data() {
      return {
        synonyms: [],
        searchedWord: '',
        emptyReturn: false
      }
    }, 
    methods: {
      async handleClick(word)  {
        try {
          this.searchedWord = word
          const response = await fetch(`https://www.dictionaryapi.com/api/v3/references/thesaurus/json/${word}?key=${process.env.VUE_APP_APIKEY}`)
          if (!response.ok) {
            throw new Error
          }
          const data = await response.json()
          const synonymsList = data[0].meta.syns[0]
          this.emptyReturn = false
          this.synonyms = synonymsList
        } catch(error) {
            this.synonyms = []
            this.emptyReturn = true
            console.log(error.message)
        }
      }
    }
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Roboto&display=swap');

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: 'Roboto', sans-serif;
  }


  #app {
    background-image: url('./assets/vue-background.jpg');
    height: 100vh;
    width: 100vw;
    background-size: 100%;
    background-repeat: none;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .app-container {
    border: 1px white solid;
    height: 80vh;
    width: 500px;
    box-shadow: inset 0 0 200px 200px rgba(255, 255, 255, 0.4);
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .title {
    background: -webkit-linear-gradient(#000, #876E5A);
    -webkit-text-fill-color: transparent;
    -webkit-background-clip: text;
    text-align: center;
    margin: 0 0 5px 0;
    font-weight: 900;
    font-size: 4rem;
    color: #000;
    margin-top: 20px;
  }

  .synonyms-for {
    text-shadow: 2px 2px 2px #999;
    font-size: 2rem;
  }

</style>


