<script setup lang="ts">
import Footer from './footer.vue';
import Header from './header.vue';

</script>

<template>
  <div>
    <Header />
    <slot />
    <Footer />
  </div>
</template>

<style scoped></style>
