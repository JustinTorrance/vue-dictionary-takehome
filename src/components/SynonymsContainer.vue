<template>
  <div>
    <div v-bind:key="synonym.id" v-for="synonym in synonyms">
      <h3>{{synonym.synonym}}</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: "SynonymsContainer",
  props: ["synonyms"]
}
</script>

<style>

</style>
