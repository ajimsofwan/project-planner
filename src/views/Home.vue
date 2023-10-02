<script setup>
import { onMounted, ref } from 'vue';
import SingleProject from '../components/SingleProject.vue'
const projects = ref([])

const getProjects = async () => {
  try {
    const response = await fetch('http://localhost:3000/projects')
    const data = await response.json()
    projects.value = data
  } catch (error) {
    console.log(error.message)
  }
}


onMounted(() => {
  getProjects()
})
</script>
<template>
  <div v-if="projects.length">
    <div v-for="project in projects" :key="project.id">
      <SingleProject :project="project" />
    </div>
  </div>
</template>
