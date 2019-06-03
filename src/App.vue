<template>
  <div id="app">
    <h1>Synonym Finder</h1>
    <Search />
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
      synonyms: [
        {
          id: 1,
          synonym: 'happy'
        },
        {
          id: 2,
          synonym: 'joy'
        },
      ]
    }
  }, 
  methods: {
    async handleClick(word)  {
      const response = await fetch(`https://www.dictionaryapi.com/api/v3/references/thesaurus/json/${word}?key=${process.env.VUE_APP_APIKEY}`)
      const data = await response.json()
      const synonyms = await data[0].meta.syns[0]
      //add word to "Synonyms for"
    }
  }
}
</script>

<style>
/* #app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */

</style>


