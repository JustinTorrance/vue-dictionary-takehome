<template>
  <div class="synonym-item" >
    <p class="synonym">{{synonym}}</p>
    <button 
      @click="$emit('handle-click', synonym)" 
      class="search-btn">
      Find Synonyms
    </button>
  </div>
</template>

<script>
  export default {
    name: "SynonymItem",
    props: ["synonym"]
  }
</script>

<style scoped>
  .synonym-item {
    background: #fff;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
    text-align: center;
    text-justify: center;
    height: 85px;
  }

  .search-btn {
    color: white;
    background-color: black;
    border-radius: 20px;
    width: 150px;
    height: 20px;
    font-size: 1rem;
    border: none;
  }

  .synonym {
    margin-bottom: 5px;
    font-size: 1.5rem;
  }

  .search-btn:hover {
    color: black;
    background-color: white;
    transition: .2s;
    cursor: pointer;
  }
</style>
