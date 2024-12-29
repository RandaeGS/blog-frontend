<script setup>
import { ref, onMounted } from 'vue'

const listArticles = ref([])

async function getData() {
  const res = await fetch("http://localhost:8080/articles")
  const finalRes = await res.json();
  listArticles.value = finalRes;
}

onMounted(() => {
  getData();
})
</script>

<template>

  <div v-if="listArticles.length === 0">
    <h1 class="text-center font-bold text-2xl py-2">No articles have been written</h1>
  </div>

  <div v-for="article in listArticles">
    <div class="border-b border-slate-200 pb-2 mb-2">
      <h1 class="text-2xl font-semibold text-slate-800">{{ article.title }}</h1>
      <h2 class="text-gray-600 pt-1">{{ article.authorName }}</h2>
    </div>

    <div class="mb-6">
      <p class="leading-relaxed">{{ article.content }}</p>

      <div class="flex gap-2 mt-4">
        <button class="px-4 py-2 bg-blue-500 hover:bg-blue-600 rounded-md text-white transition-colors">Update</button>
        <button class="px-4 py-2 bg-red-500 hover:bg-red-600 rounded-md text-white transition-colors">Delete</button>
      </div>
    </div>
  </div>

</template>
