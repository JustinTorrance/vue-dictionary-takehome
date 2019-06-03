<template>
  <div v-bind:searchInput="searchInput">
    <form @submit.prevent>
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
    </form>
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
±