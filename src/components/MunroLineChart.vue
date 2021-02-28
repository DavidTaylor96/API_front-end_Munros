<template>
  <div class="component-wrapper">
    <GChart
    v-if="chartData"
    type="LineChart"
    :data="chartData"
    :options="chartOptions"
    />
  </div>
</template>

<script>
import { GChart } from 'vue-google-charts'

export default {
  name: 'munro-line-graph',
  components:{ GChart },
data () {
    return {
      chartOptions:{
        chart:{
          titel: 'Munro Heights',
          subtitle: 'Munro, Height, In Feet'
        }
      }
    }
   }, 
  props:['mixData'],

  computed: {
    chartData: function () {
      if(this.mixData){
        const chartData = [['height'], ...this.mixData.map(mix => ([mix.height]))]
        return chartData
      }
        return null 
    }
  }
}
</script>

<style>

</style>