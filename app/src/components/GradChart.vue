<template>
  <script src="https://data.cityofnewyork.us/resource/ynqa-y42e.json"></script>
  <body>
    <canvas id="myChart" style="width: 100%; max-width: 600px"></canvas>

    <script>
      var xValues = [item.borough]
      var yValues = [item.total_cohort]
      var barColors = ['red', 'green', 'blue', 'orange', 'brown']

      new Chart('myChart', {
        type: 'bar',
        data: {
          labels: xValues,
          datasets: [
            {
              backgroundColor: barColors,
              data: yValues,
            },
          ],
        },
        options: {
          legend: { display: false },
          title: {
            display: true,
            text: 'World Wine Production 2018',
          },
        },
      })
    </script>
  </body>
</template>

<script setup></script>

<style lang="scss" scoped></style>
