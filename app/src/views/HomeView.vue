<script setup>
async function GetGrad() {
  let res = await fetch('https://data.cityofnewyork.us/resource/ynqa-y42e.json')
  let data = await res.json()
  graduation.value = data.results
  console.log(data.results)
}
</script>

<template>
  <main></main>
</template>
