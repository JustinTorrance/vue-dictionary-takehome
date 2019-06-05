<template>
  <div v-bind:searchInput="searchInput">
    <form @submit.prevent>
      <input 
        type="text"
        placeholder="Search"
        v-model="searchInput"
        class="search-input"
        autofocus
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

.search-input {
  width: 300px;
  height: 35px;
  font-size: 1.7rem;
  border-radius: 20px 0 0 20px ;
  outline: none;
  padding-left: 10px;
  border: none;
}

.search-input::placeholder {
  font-size: 1.7rem;
}

.search-btn {
  color: white;
  background-color: black;
  border-radius: 0 20px 20px 0;
  width: 100px;
  height: 35px;
  font-size: 1rem;
  border: none;
}

.search-btn:hover {
  color: black;
  background-color: white;
  transition: .2s;
  cursor: pointer;
}

form {
  display: flex;
  align-items: center;
  height: 35px;
  margin: 20px 0;
}

</style>
