<script setup>
import { ref, onMounted } from 'vue'

const graduation = ref([])

async function GetGrad() {
  try {
    let res = await fetch('https://data.cityofnewyork.us/resource/ynqa-y42e.json')
    let data = await res.json()

    console.log('Fetched Data:', data)

    if (Array.isArray(data) && data.length > 0) {
      graduation.value = data
    } else {
      console.error('Data is empty or not in expected format')
    }
  } catch (error) {
    console.error('Error fetching data: ', error)
  }
}

onMounted(() => {
  GetGrad()
})
</script>

<template>
  <RouterLink to="/about">Menu</RouterLink>
  <main>
    <div v-if="graduation.length > 0">
      <h1>Graduation Data</h1>
      <ul>
        <li v-for="(item, index) in graduation" :key="index">
          {{ item.borough }} <br />
          {{ item.cohort_year }} <br />
        </li>
      </ul>
    </div>
    <div v-else>
      <p>Loading data...</p>
    </div>
  </main>
</template>

<style scoped></style>
