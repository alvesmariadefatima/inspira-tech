<template>
  <div id="app">
    <Home />
    <Footer />
  </div>
</template>

<script>
import Home from '../src/views/Home.vue'
import Footer from './components/Footer.vue';

export default {
  components: {
    Home,
    Footer
  }
};
</script>

<style scoped>

</style>
