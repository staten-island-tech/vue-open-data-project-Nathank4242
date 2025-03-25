<script setup>
import { ref, onMounted } from 'vue'
import { RouterLink } from 'vue-router'

const filteredData = ref([])

const fetchChartData = async () => {
  try {
    const response = await fetch('https://data.cityofnewyork.us/resource/ynqa-y42e.json')
    if (!response.ok) {
      throw new Error('Network response was not ok')
    }
    const apiData = await response.json()

    filteredData.value = apiData
  } catch (error) {
    console.error('Error fetching data:', error)
  }
}

onMounted(() => {
  fetchChartData()
})
</script>

<template>
  <div>
    <RouterLink to="/about">Drop Out Rates</RouterLink>
    <h2>WOW Data</h2>

    <div>
      <div v-for="(item, index) in filteredData" :key="index" class="card">
        <div class="card-content">
          <h3 class="card-title">{{ item.borough }}</h3>
          <p><strong>Cohort Year:</strong> {{ item.cohort_year }}</p>
          <p><strong>Number of Graduates:</strong> {{ item.grads }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card {
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 16px;
  margin: 10px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  width: 250px;
  display: inline-block;
}

.card-content {
  text-align: center;
}

.card-title {
  font-size: 1.5rem;
  margin-bottom: 10px;
}

.card p {
  font-size: 1rem;
  margin: 5px 0;
}
</style>
