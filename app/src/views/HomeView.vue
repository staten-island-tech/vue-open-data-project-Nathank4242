<script setup>
import { ref, onMounted } from 'vue'

const graduation = ref([])

async function GetGrad() {
  let res = await fetch('https://data.cityofnewyork.us/resource/ynqa-y42e.json')
  let data = await res.json()
  graduation.value = data
  console.log(data)
}
onMounted(() => {
  GetGrad()
})
</script>

<template>
  <main>
    <div v-if="graduation.length > 0">
      <h1>Graduation Data</h1>
      <ul>
        <li v-for="(item, index) in graduation" :key="index">
          {{ item.school_name }} - {{ item.graduation_rate }}
        </li>
      </ul>
    </div>
    <div v-else>
      <p>Loading data...</p>
    </div>
  </main>
</template>

<style scoped></style>
