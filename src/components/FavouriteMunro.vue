<template>
  <div>
    <div class="bagged" v-for="(baggedMunro, index) in baggedMunro" :key="index">
    <h3>Name: {{baggedMunro.name}}</h3>
    <p>Height: {{baggedMunro.height}}ft</p> 
    <p>Region: {{baggedMunro.region}}</p>
    <input type="submit" value="delete" v-on:click="removeMunro">
    </div>
  </div>
</template>

<script>

export default {
  name: 'bagged-munro',
  props: ['baggedMunro'],

  methods: {
   removeMunro: function(index){
     return this.baggedMunro.splice(index, 1)
   }
  }
}
</script>

<style>
.bagged{
}


</style>