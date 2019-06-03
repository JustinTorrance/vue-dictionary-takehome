<template>
  <div id="app">
    <h1>Synonym Finder</h1>
    <Search v-on:handle-click="handleClick" />
    <h3>Synonyms for: {{ searchedWord }}</h3>
    <SynonymsContainer v-bind:synonyms="synonyms" v-on:handle-click="handleClick" />
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
        searchedWord: ''
      }
    }, 
    methods: {
      async handleClick(word)  {
        this.searchedWord = word
        const response = await fetch(`https://www.dictionaryapi.com/api/v3/references/thesaurus/json/${word}?key=${process.env.VUE_APP_APIKEY}`)
        const data = await response.json()
        const synonymsList = await data[0].meta.syns[0]
        this.synonyms = synonymsList

        //add word to "Synonyms for"
      }
    }
  }
</script>

<style>

</style>


