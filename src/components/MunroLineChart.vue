<template>
  <div class="chart-wrapper">
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
      chartOptions:{
        width: 800,
        height: 470,
        chart:{
          title: 'Munro Heights',
          subtitle: 'Munro, Height, In Feet'
        }
      },
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
.chart-wrapper{
  float: right;
  margin-top: 10px;
  margin-bottom: 5px;
  margin-right: 10px
}

</style>