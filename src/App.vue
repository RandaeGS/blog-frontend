<script setup>
import listBlogs from './components/listBlogs.vue'

</script>

<template>
  <div class="min-h-screen bg-gray-50 flex flex-col">

    <nav class="bg-indigo-600 shadow-md">
      <div class="font-semibold flex">
        <a class="p-4 hover:bg-indigo-700 transition-colors text-white">List</a>
        <a class="p-4 hover:bg-indigo-700 transition-colors text-white">Create</a>
      </div>
    </nav>

    <main>
      <listBlogs />
    </main>
  </div>
</template>

<style scoped></style>
