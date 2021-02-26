<template>
  <div>
    <select v-on:change="handleSelect" v-model="selectedMunro">
     <option v-for="(munro, index) in munros" :value="munro" :key="index">{{munro.name}}</option>
    </select>
  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'Munro-list',
  props: ['munros'],

  data(){
    return{
      selectedMunro: [],
    }
  },
  methods: {
    handleSelect() {
      eventBus.$emit('munro-selected', this.selectedMunro)
    }
  }
}
</script>

<style>

</style>