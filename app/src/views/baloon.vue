<template>
    <GradChart />
    <nav>
      <RouterLink to="/about">Menu</RouterLink>
    </nav>
  </template>
  
  <script>
  import GradChart from '@/components/GradChart04.vue'
  
  export default {
    name: 'App',
    components: { GradChart },
  }
  </script>