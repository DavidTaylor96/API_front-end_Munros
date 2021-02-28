<template>
  <div>
    <h1 id="heading">Chose Your Munro</h1>
    <div id="forms">
      <filter-munro-form :munros="munros"></filter-munro-form>
      <munro-list :munros="munros"></munro-list>
    </div>
    <div id="details">
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
body{
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
  background-color: #f4f4f4;
}

#heading{
  margin: 0;
  text-align: center;
  font-weight: 100;
  background-color: rgb(31, 101, 129);
  color: white;
  padding: 20px;
}

button{
  padding: 10px;
  border: none;
  background-color: rgb(31, 101, 129);
  color: white;
  border-radius: 5px;
  margin-left: 45%;
  margin-top: 5px;
}

#forms{
  margin: 5px;
  display: flex;
  flex-flow: column wrap;
  align-items: center;
}

#details{
  display: flex;
  flex-flow: row wrap;
  justify-content: center;
  box-shadow:  2px 2px 2px 0px rgb(20, 53, 66);
  margin: 0 200px;
}
</style>
