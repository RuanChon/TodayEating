<template>
  <div id="app">
    <EatWhat />
  </div>
</template>

<script>
import EatWhat from './components/eatWhat.vue'

export default {
  name: 'App',
  components: {
    EatWhat
  }
}
</script>

<style lang="scss">
#app {
  margin: 0;
  padding: 0;
}
</style>
