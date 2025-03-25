<template>
  <Bar id="my-chart-id" :options="chartOptions" :data="chartData" />
</template>

<script>
import { Bar } from 'vue-chartjs'
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
} from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'GradChart',
  components: { Bar },
  data() {
    return {
      chartData: {
        labels: [],
        datasets: [
          {
            label: 'Drop Out rates',
            data: [],
            backgroundColor: 'rgba(75, 192, 192, 0.2)',
            borderColor: 'rgba(75, 192, 192, 1)',
            borderWidth: 1,
          },
        ],
      },
      chartOptions: {
        responsive: true,
        plugins: {
          title: {
            display: true,
            text: 'Drop Outs by Borough',
          },
        },
        scales: {
          x: {
            title: {
              display: true,
              text: 'Boroughs',
            },
          },
          y: {
            title: {
              display: true,
              text: 'Drop Out Numbers',
            },
            beginAtZero: true,
          },
        },
      },
    }
  },
  mounted() {
    this.fetchChartData()
  },
  methods: {
    async fetchChartData() {
      try {
        // Using the native fetch API instead of axios
        const response = await fetch('https://data.cityofnewyork.us/resource/ynqa-y42e.json')
        if (!response.ok) {
          throw new Error('Network response was not ok')
        }
        const apiData = await response.json()

        const filteredData = apiData.filter((item) => item.cohort_year === '2003')
        const labels = filteredData.map((item) => item.borough)
        const data = filteredData.map((item) => item.dropout)

        this.chartData = {
          labels: labels,
          datasets: [{ label: 'Drop Out rates (2003)', data: data }],
        }
      } catch (error) {
        console.error('Error fetching data:', error)
      }
    },
  },
}
</script>

<style lang="scss" scoped></style>
