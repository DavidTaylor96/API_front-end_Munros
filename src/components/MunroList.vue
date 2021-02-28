<template>
  <div>
    <select id="option-bar" v-on:change="handleSelect(index)" v-model="selectedMunro">
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
    handleSelect(index) {
      eventBus.$emit('munro-selected', this.selectedMunro, index)
    }
  }
}
</script>

<style>
#option-bar{
  padding: 7px;
  border: 1px solid rgb(183, 183, 183);
  border-radius: 5px;
  margin: 5px;
}

</style>