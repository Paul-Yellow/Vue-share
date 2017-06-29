<template>
  <div id="app">
    <test-item></test-item>
  </div>
</template>

<script>
import TestItem from '../components/test.vue';
export default {
  name: 'app',
  data() {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  components: { TestItem },
}
</script>

<style>

</style>
