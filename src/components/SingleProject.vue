<script setup>
import { ref } from 'vue';

defineProps(['project'])

const showDetail = ref(false)

function handleShow() {
  showDetail.value = !showDetail.value
}
</script>
<template>
  <div class="max-w-xl mx-auto mb-2 cursor-pointer group" @click="handleShow">
    <div class="overflow-hidden bg-white rounded-xl group-hover:bg-blue-600 dark:bg-gray-800">
      <div class="flex">
        <div class="flex-none w-1 bg-blue-600 group-hover:bg-blue-400"></div>
        <div class="flex-1 px-6 py-6 text-left">
          <h1 class="text-2xl font-bold text-blue-600 group-hover:text-white">{{ project.title }}</h1>
          <div v-show="showDetail">
            <p class="text-gray-700 group-hover:text-white dark:text-gray-300"><span>{{ project.detail }}</span>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>