<template>
  <form v-on:submit.prevent>
    <input id="form-bar" type="text" v-model="search" placeholder="Search For Munro" v-on:keyup="searchForMunro">
  </form>
</template>

<script>
import MunroList from './MunroList.vue'

import { eventBus } from '../main.js'

export default {
  name: "filter-munro-form",
  props: ['munros'],

  data(){
    return{
      "search": "",
      "selectedMunro": []
    }
  },
  methods: {
    searchForMunro(){
      let foundMunro = this.munros.find((munro) => {
        return munro.name.toLowerCase().indexOf(this.search.toLowerCase()) > -1
      })
      this.selectedMunro = foundMunro

      eventBus.$emit('munro-selected', this.selectedMunro)
    },
  },
  components:{
    'munro-list': MunroList,
  }
}
</script>

<style>

#form-bar{
  padding: 7px 75px;
  border: 1px solid rgb(183, 183, 183);
  border-radius: 5px;
}



</style>