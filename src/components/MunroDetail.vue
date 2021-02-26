<template>
  <div>
    <div v-if="!munro">
      <p>Please Select a Munro</p>
    </div>
    <div v-if="munro">
      <h3>Name: {{munro.name}}</h3>
      <p>Height: {{munro.height}}ft</p>
      <p>Region: {{munro.region}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'munro-detail',
  props: ['munro']

}
</script>

<style>

</style>