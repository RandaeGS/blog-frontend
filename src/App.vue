<script setup>
import listBlogs from './components/listBlogs.vue'
import createBlog from './components/createBlog.vue'

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
      <div class="flex-1 flex justify-center p-6 bg-slate-100 shadow-md min-w-max items-center">
        <div class="w-full max-w-4xl mx-auto">

          <listBlogs />
          <createBlog />
        </div>
      </div>
    </main>
  </div>
</template>

<style scoped></style>
