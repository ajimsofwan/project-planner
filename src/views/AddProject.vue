<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
const router = useRouter()
const title = ref(null)
const details = ref(null)

function handleSubmit() {
  const project = {
    title: title.value,
    details: details.value,
    complete: false
  }
  addProject(project)
}

const addProject = async (data) => {
  try {
    const response = await fetch('http://localhost:3000/projects', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(data)
    })
    if (response.ok) {
      router.push('/')
    }
  } catch (error) {
    console.log(error.message)
  }
}

</script>
<template>
  <div
    class="max-w-xl p-6 mx-auto bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700">
    <form @submit.prevent="handleSubmit">
      <div class="mb-6">
        <label for="title" class="block mb-2 text-sm font-medium text-left text-gray-900 dark:text-white">TITLE:</label>
        <input v-model="title" type="text" id="title"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:outline-none focus:ring-1 focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="Title" required>
      </div>
      <div class="mb-6">
        <label for="details"
          class="block mb-2 text-sm font-medium text-left text-gray-900 dark:text-white">DETAILS:</label>
        <textarea v-model="details" id="details" rows="4"
          class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border focus:outline-none focus:ring-1 border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="Add some details..." required></textarea>
      </div>
      <button type="submit"
        class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">Add
        Project</button>
    </form>
  </div>
</template>