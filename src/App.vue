<template>
  <div>
    <Home />
    <Footer />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Home from './components/Home.vue'
import Footer from './components/Footer.vue'

export default defineComponent({
  name: 'App',
  components: {
    Home,
    Footer
  }
})
</script>
