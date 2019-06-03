<template>
  <div v-bind:searchInput="searchInput">
      <input 
        type="text"
        placeholder="Search"
        v-model="searchInput"
      >
      <button
        @click="$emit('handle-click', searchInput)" 
        type="submit"
        class="search-btn"
      >
        Search
      </button>
      <br />
      <p>{{ searchInput }}</p>
  </div>
</template>

<script>
  export default {
    name: "Search",
    props: {

    },
    data() {
      return {
        searchInput: ''
      }
    }
  }
</script>

<style scoped>

</style>
