<template>
  <div id="app">
    <h1>Synonym Finder</h1>
    <Search v-on:handle-click="handleClick" />
    <h3>Synonyms for: {{ searchedWord }}</h3>
    <SynonymsContainer v-bind:synonyms="synonyms" v-on:handle-click="handleClick" />
    <h3 v-if="emptyReturn">Sorry, there are no synonyms for this word</h3>
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

</style>


