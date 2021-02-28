<template>
  <div id="set-form">
    <div class="bagged" v-for="(baggedMunro, index) in baggedMunro" :key="index">
    <h3>Name: {{baggedMunro.name}}</h3>
    <p>Height: {{baggedMunro.height}}ft</p> 
    <p>Region: {{baggedMunro.region}}</p>
    <input  id="delete" type="submit" value="delete" v-on:click="removeMunro">
    </div>
  </div>
</template>

<script>

export default {
  name: 'bagged-munro',
  props: ['baggedMunro'],

  methods: {
   removeMunro: function(index){
     return this.baggedMunro.splice(index, 0)
   }
  }
}
</script>

<style>
.bagged{
  margin: 20px;
  width: 40%;
  box-shadow: 2px 0px 3px 0px rgb(20, 53, 66);
}
#set-form{
  display: flex;
  flex-flow: row wrap;
}

#delete{
  padding: 10px;
  border: none;
  background-color: rgb(31, 101, 129);
  color: white;
  border-radius: 5px;
  margin-top: 5px;
}

</style>