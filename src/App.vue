<template>
  <div class="app">
    <Dashboard/>
  </div>
</template>

<script>
import Dashboard from './components/Dashboard/index.vue'
export default {
  name: 'App',
  components: {
    Dashboard,
  },
  data() {
    return {

    }
  }
}
</script>

<style scoped>
.app {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}
</style>
