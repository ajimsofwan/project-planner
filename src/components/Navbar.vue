<template>
  <div
    class="max-w-xl mx-auto mb-5 text-sm font-medium text-gray-500 border-b border-gray-200 dark:text-gray-400 dark:border-gray-700">
    <ul class="flex flex-wrap justify-center -mb-px">
      <li class="mr-2">
        <router-link :to="{ name: 'Home' }"
          class="inline-block p-4 border-b-2 border-transparent rounded-t-lg hover:text-gray-600 hover:border-gray-300 dark:hover:text-gray-300"
          aria-current="page">
          Projects
        </router-link>
      </li>
      <li class="mr-2">
        <router-link :to="{ name: 'AddProject' }"
          class="inline-block p-4 border-b-2 border-transparent rounded-t-lg hover:text-gray-600 hover:border-gray-300 dark:hover:text-gray-300">
          Add New Project
        </router-link>
      </li>
    </ul>
  </div>
</template>
<style scoped>
.router-link-active {
  @apply text-blue-600 border-b-2 border-blue-600 dark:text-blue-500 dark:border-blue-500;
}
</style>
