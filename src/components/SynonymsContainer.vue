<template>
  <div>
    <div v-bind:key="synonym.id" v-for="synonym in synonyms">
      <SynonymItem v-bind:synonym="synonym" v-on:handle-click="$emit('handle-click', synonym.synonym)" />
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

<style>

</style>
