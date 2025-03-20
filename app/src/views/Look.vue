<template>
  <GradChart />
  <nav>
    <RouterLink to="/about">Menu</RouterLink>
  </nav>
</template>

<script>
import GradChart from '@/components/GradChart01.vue'

export default {
  name: 'App',
  components: { GradChart },
}
</script>
