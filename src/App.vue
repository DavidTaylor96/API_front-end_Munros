<template>
  <div>
    <h1>Chose Your Munro</h1>
    <div>
      <filter-munro-form :munros="munros"></filter-munro-form>
      <munro-list :munros="munros"></munro-list>
      <munro-detail :munro="selectedMunro"></munro-detail>
    </div>
    
    <button v-if="!baggedMunro.includes(selectedMunro)" v-on:click="addToFavourite">Bag Munro</button>
    <bagged-munro :baggedMunro="baggedMunro"></bagged-munro>

  </div>
</template>

<script>
import FilterMunroForm from './components/FilterMunroForm.vue'
import MunroDetail from './components/MunroDetail.vue';
import MunroList from './components/MunroList.vue';
import BaggedMunro from './components/FavouriteMunro.vue'

import { eventBus } from './main.js'

export default {
  name: 'app',
  data(){
    return{
      munros: [],
      selectedMunro: null,
      baggedMunro: [],
    }
  },
  components:{
    'munro-list': MunroList,
    'munro-detail': MunroDetail,
    'bagged-munro': BaggedMunro,
    'filter-munro-form': FilterMunroForm
  },
  mounted() {
    this.getNewListItems();

    eventBus.$on('munro-selected', (munro) => {
      this.selectedMunro = munro
    })
  },
  methods: {
    getNewListItems() {
      fetch("https://munroapi.herokuapp.com/munros")
       .then(res => res.json())
       .then(data => this.munros = data)
    },
    addToFavourite: function () {
      if(!this.selectedMunro) return;
      this.baggedMunro.push(this.selectedMunro)
    }
  }
}
</script>

<style>

</style>
