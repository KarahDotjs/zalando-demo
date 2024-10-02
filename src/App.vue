<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
</script>
<template>
  <Header />
  <main>
    <div class="container">
      <div></div>
      <div></div>
    </div>
  </main>
  <Footer />
</template>

<style scoped>
.container {
  display: flex;
  height: calc(
    100vh - var(--header-top-height) - var(--header-bottom-height) - var(--footer-height));
  /* To avoid scrolling */
}
.container > div {
  width: 50%;
  border: 1px solid green;
}
</style>
