<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
</script>
<template>
  <!-- Appel du composant Header -->
  <Header />
  <main>
    <!-- Wrapper -->
    <div class="container">
      <!-- Première colonne -->
      <div>
        <!-- L'image sera ajoutée dans le chapitre qui lui est dédié -->
      </div>
      <!-- Deuxième colonne -->
      <div>
        <!-- Le contenue sera ajouté au fur et à mesure des notions abordées -->
      </div>
    </div>
  </main>
  <!-- Appel du composant Footer -->
  <Footer />
</template>

<style scoped>
.container {
  display: flex;
  height:calc(100vh - var(--header-top-height) - var(--header-bottom-height) - var(--footer-height));
}
.container > div {
  width: 50%;
  border: 1px solid green;
  
}
</style>

