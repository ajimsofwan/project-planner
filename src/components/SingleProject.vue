<script setup>
import { ref } from 'vue';

const props = defineProps(['project'])

const showDetails = ref(false)

const emit = defineEmits(['update', 'delete'])

function handleShow() {
  showDetails.value = !showDetails.value
}

const deleteProject = async () => {
  try {
    const response = await fetch('http://localhost:3000/projects/' + props.project.id, { method: 'DELETE' })
    if (response.ok) {
      emit('delete', props.project.id)
    }
  } catch (error) {
    console.log(error.message)
  }
}

</script>
<template>
  <div class="max-w-xl mx-auto mb-2 cursor-pointer group">
    <div class="overflow-hidden bg-white rounded-xl hover:bg-slate-50 dark:hover:bg-slate-700 dark:bg-slate-800">
      <div class="flex">
        <div class="flex-none w-1 bg-blue-600"></div>
        <div class="flex items-center justify-between flex-1 px-6 py-6 text-left">
          <div @click="handleShow">
            <h1 class="text-2xl font-bold text-blue-600">{{ project.title }}
            </h1>
            <div v-show="showDetails">
              <p class="text-gray-700 dark:text-gray-300"><span>{{ project.detail }}</span>
              </p>
            </div>
          </div>
          <div>
            <span class="mx-1 material-icons text-slate-400 hover:text-slate-500 dark:hover:text-slate-300">done</span>
            <span class="mx-1 material-icons text-slate-400 hover:text-slate-500 dark:hover:text-slate-300">edit</span>
            <span @click="deleteProject"
              class="mx-1 material-icons text-slate-400 hover:text-slate-500 dark:hover:text-slate-300">delete</span>

          </div>
        </div>
      </div>
    </div>
  </div>
</template>