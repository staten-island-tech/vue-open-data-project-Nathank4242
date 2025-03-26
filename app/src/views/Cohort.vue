<template>
  <div>
    <nav>
      <RouterLink to="/about">Menu</RouterLink>
    </nav>
    <ScatterPlot />
  </div>
</template>

<script>
import ScatterPlot from '@/components/ScatterPlot.vue'

export default {
  name: 'App',
  components: {
    ScatterPlot,
  },
}
</script>

<style scoped></style>
