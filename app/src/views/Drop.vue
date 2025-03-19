<template>
  <GradChart />
  <nav>
    <RouterLink to="/">Home</RouterLink>
  </nav>
</template>

<script>
import GradChart from '@/components/GradChart.vue'

export default {
  name: 'App',
  components: { GradChart },
}
</script>
