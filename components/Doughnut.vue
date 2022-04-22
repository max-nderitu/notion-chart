<template>
  <Doughnut :chart-data="chartData"  />
</template>

<script lang="ts">
import { defineComponent,h, PropType }  from 'vue'
import { Doughnut } from 'vue-chartjs'
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  ArcElement,
  CategoryScale,
  Plugin
} from 'chart.js'

// import axios from 'axios'
// import { API_URL } from '~/configs/config'

ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale)

export default defineComponent({
  name: 'DoughnutChart',
  components: {
    Doughnut
  },
  props: {
    chartId: {
      type: String,
      default: 'doughnut-chart'
    },
    // width: {
    //   type: Number,
    //   default: 400
    // },
    // height: {
    //   type: Number,
    //   default: 400
    // },
    cssClasses: {
      type: String,
      default: 'dark-mode'
    },
    styles: {
      type: Object as PropType<Partial<CSSStyleDeclaration>>,
      default: () => {}
    },
    plugins: {
      type: Array as PropType<Plugin<'doughnut'>[]>,
      default: () => []
    }
  },
  setup(props) {
    const chartData = {
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
    }

    const chartOptions = {
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

    return () =>
        h(Doughnut, {
          chartData,
          chartOptions,
          chartId: props.chartId,
          // width: props.width,
          // height: props.height,
          cssClasses: props.cssClasses,
          styles: props.styles,
          plugins: props.plugins
        })
  }
})

</script>

<style scoped>
.dark-mode {
  @apply h-screen w-screen
  background: #191919;
}
</style>
