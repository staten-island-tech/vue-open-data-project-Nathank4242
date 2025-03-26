<template>
  <div>
    <scatter-chart :data="chartData" :options="chartOptions" height="500" width="800" />
  </div>
</template>

<script>
import { defineComponent } from 'vue'
import { Scatter } from 'vue-chartjs'
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  CategoryScale,
  LinearScale,
  PointElement,
  ArcElement,
} from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, CategoryScale, LinearScale, PointElement, ArcElement)

export default defineComponent({
  name: 'ScatterPlot',
  components: {
    ScatterChart: Scatter,
  },
  data() {
    return {
      chartData: {
        datasets: [
          {
            label: 'Number of Kids in Cohorts by Borough (2001)',
            data: [
              { x: 300, y: 1, label: 'Manhattan' },
              { x: 450, y: 2, label: 'Brooklyn' },
              { x: 600, y: 3, label: 'Queens' },
              { x: 250, y: 4, label: 'Bronx' },
              { x: 200, y: 5, label: 'Staten Island' },
            ],
            backgroundColor: [
              'rgba(75, 192, 192, 0.5)',
              'rgba(255, 99, 132, 0.5)',
              'rgba(153, 102, 255, 0.5)',
              'rgba(255, 159, 64, 0.5)',
              'rgba(54, 162, 235, 0.5)',
            ],
            borderColor: [
              'rgba(75, 192, 192, 1)',
              'rgba(255, 99, 132, 1)',
              'rgba(153, 102, 255, 1)',
              'rgba(255, 159, 64, 1)',
              'rgba(54, 162, 235, 1)',
            ],
            borderWidth: 2,
          },
        ],
      },
      chartOptions: {
        responsive: true,
        scales: {
          x: {
            type: 'linear',
            position: 'bottom',
            title: {
              display: true,
              text: 'Number of Kids in Cohort (2001)',
            },
          },
          y: {
            type: 'category',
            labels: ['Manhattan', 'Brooklyn', 'Queens', 'Bronx', 'Staten Island'],
            title: {
              display: true,
              text: 'Boroughs',
            },
          },
        },
        plugins: {
          tooltip: {
            backgroundColor: '#fff',
            titleColor: '#000',
            bodyColor: '#000',
            borderColor: '#000',
            borderWidth: 1,
          },
        },
      },
    }
  },
})
</script>

<style scoped></style>
