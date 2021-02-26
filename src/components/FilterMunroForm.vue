<template>
  <form v-on:submit.prevent>
    <input type="text" v-model="search" placeholder="Search For Munro" v-on:keyup="searchForMunro">
  </form>
</template>

<script>
import MunroList from './MunroList.vue'

import { eventBus } from '../main.js'

export default {
  name: "filter-munro-form",
  props: ['munros'],
  
  methods: {
    searchForMunro(){
      let foundMunro = this.munro.find((munro) => {
        return munro.name.toLowerCase().indexOf(this.search.toLowerCase()) > -1
      })
      this.selectedMunro = foundMunro

      eventBus.$$emit('munro-selected', this.selectedMunro)
    }
  },
  components:{
    'munro-list': MunroList,
  }
}
</script>

<style>

</style>