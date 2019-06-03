<template>
  <div id="app">
    <h1>Synonym Finder</h1>
    <Search />
    <SynonymsContainer v-bind:synonyms="synonyms" />
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
