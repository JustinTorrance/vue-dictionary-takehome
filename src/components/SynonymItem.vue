<template>
  <div class="synonym-item" >
    <p>{{synonym}}</p>
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
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }
</style>
