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
    handleClick(word) {
      //add word to query string
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
