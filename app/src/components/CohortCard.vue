<template>
  <div>
    <canvas ref="myCircleChart" width="400" height="400"></canvas>
    <nav>
      <RouterLink to="/about">Menu</RouterLink>
    </nav>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import { Chart } from 'chart.js'

const myCircleChart = ref(null)

onMounted(() => {
  if (myCircleChart.value) {
    new Chart(myCircleChart.value, {
      type: 'doughnut',
      data: {
        labels: ['Red', 'Blue', 'Yellow'],
        datasets: [
          {
            label: 'My First Dataset',
            data: [300, 50, 100],
            backgroundColor: ['rgb(255, 99, 132)', 'rgb(54, 162, 235)', 'rgb(255, 205, 86)'],
            hoverOffset: 4,
          },
        ],
      },
      options: {
        responsive: true,
        plugins: {
          legend: {
            position: 'top',
          },
          tooltip: {
            callbacks: {
              label: function (tooltipItem) {
                return tooltipItem.raw + ' units'
              },
            },
          },
        },
      },
    })
  }
})
</script>

<style scoped>
div {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

canvas {
  max-width: 100%;
  max-height: 100%;
}
</style>
