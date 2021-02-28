<template>
  <div class="component-wrapper">
    <GChart
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
      // chartData:[
      // ['name', 'height'],
      // ['Carin Groms', 1244],
      // ['Ben Nevs', 1305],
      // ['Ben Macdui', 1309],
      // ],
      chartOptions:{
        chart:{
          title: 'Munro Heights',
          subtitle: 'Munro, Height, In Feet'
        }
      },
      // munroMixData: [],
    }
   }, 
  props:['mixData'],

  computed: {
    chartData: function () {
      if(this.mixData){
      const chartData = [['name','height'], ...this.mixData.map(mix => ([mix.name, mix.height]))]
      return chartData
      }
      return null
    }
  }
}
</script>

<style>

</style>