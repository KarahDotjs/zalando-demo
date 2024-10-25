<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Details from './components/Details.vue'

import data from './assets/data.json'

import { reactive, ref } from 'vue'
// accepted object & array
const productInfos = reactive(data)
// all types of values must simple
const selectedVariant = ref(data.variants[0])
</script>

<template>
  <div>
    <Header />
    <main>
      <div class="container">
        <div></div>

        <Details :productInfos="productInfos" :selectedVariant />
      </div>
    </main>

    <Footer />
  </div>
</template>

<style scoped>
.container {
  display: flex;
  height: calc(
    100vh - var(--header-top-height) - var(--header-bottom-height) - var(--footer-height)
  );
  /* To avoid scrolling */
}
.container > div {
  width: 50%;
  border: 1px solid green;
}
.container > div:last-child {
  padding: 25px 0 25px 100px;
  box-sizing: border-box;
}
/* La balise 'p' se trouvant immediatement après la balise 'h1' */
</style>
