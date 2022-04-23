<template>
  <DoughnutChart :chartData="chartData" :options="chartOptions" />
</template>

<script lang="ts">
import { defineComponent}  from 'vue'
import { DoughnutChart } from 'vue-chart-3'

// import axios from 'axios'
// import { API_URL } from '~/configs/config'

export default defineComponent({
  name: 'Doughnut',
  components: { DoughnutChart },
  setup () {
    return {
      chartData: {
        labels: ["To be done", "Missed Target", "Partially Achieved", "Achieved"],
        datasets: [
          {
            label: "OKR Progress",
            labelColor: "white",
            data: [1, 1, 1, 1],
            backgroundColor: [
              'rgba(227, 199, 90, 1)',
              'rgba(223, 84, 82, 1)',
              'rgba(94, 135, 201, 1)',
              'rgba(82, 158, 114, 1)'
            ],
            borderColor: [
              'rgba(227, 199, 90, 1)',
              'rgba(223, 84, 82, 1)',
              'rgba(94, 135, 201, 1)',
              'rgba(82, 158, 114, 1)'
            ],
            borderWidth: 1
          }
        ],
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
          legend: {
            display: true,
            position: "bottom",
            align: "center",
            fontFamily: "Allianz-Neo",
            textDirection: 'ltr',
            labels: {
              usePointStyle: true,
              pointStyle: "rectRounded",
              color: "white",
            }
          }
        }
      }
    }
  }
})

</script>

<style scoped>
</style>
