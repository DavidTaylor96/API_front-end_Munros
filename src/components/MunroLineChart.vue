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
      chartData:[
      ['Munro', 'Height'],
      ['Carin Gorm', 1244],
      ['Cairn Toul', 1294]
      ],
    chartOptions:{
      chart:{
        titel: 'Munro Heights',
        subtitle: 'Munro, Height, In Feet'
      }
    }
    }
   }
}
</script>

<style>

</style>