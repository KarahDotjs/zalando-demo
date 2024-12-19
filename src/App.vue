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
        <div><img :src="selectedVariant.image.url" :alt="selectedVariant.image.alt" /></div>

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
  /* border: 1px solid green; */
}
.container > div:last-child {
  padding: 25px 0 25px 100px;
  box-sizing: border-box;
}
.container > div:first-child {
  padding: 25px;
}
img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
/* -- Deuxième colonne ----------- */
/* [...] */
/* La balise 'p' se trouvant immediatement après la balise 'h1' */
</style>
