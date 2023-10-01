<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div class="flex items-center justify-center h-screen text-center">
    <div>
      <div class="flex justify-center"><a href="https://vitejs.dev" target="_blank">
          <img src="/vite.svg" class="w-20 mx-1" alt="Vite logo" />
        </a>
        <a href="https://vuejs.org/" target="_blank">
          <img src="./assets/vue.svg" class="w-20 mx-1" alt="Vue logo" />
        </a>
      </div>
      <HelloWorld msg="Vite + Vue" />
    </div>
  </div>
</template>