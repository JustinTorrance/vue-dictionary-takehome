<template>
  <div class="wrapper">
    <div v-bind:key="synonym.id" v-for="synonym in synonyms">
      <SynonymItem v-bind:synonym="synonym" v-on:handle-click="$emit('handle-click', synonym)" />
    </div>
  </div>
</template>

<script>
  import SynonymItem from './SynonymItem'

  export default {
    name: "SynonymsContainer",
    components: {
      SynonymItem
    },
    props: ["synonyms"],
  }
</script>

<style scoped>

  .wrapper {
    margin: 20px 0;
    overflow-y: scroll;
    width: 300px;
    border-radius: 20px;
  }

</style>
