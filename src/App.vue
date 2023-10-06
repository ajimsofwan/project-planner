<script setup>
import Navbar from './components/Navbar.vue';
</script>
<template>
  <section class="px-5 py-10 text-center">
    <Navbar />
    <router-view />
  </section>
</template>