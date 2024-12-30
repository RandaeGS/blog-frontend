<script setup>
import { ref } from 'vue'
import listBlogs from './components/listBlogs.vue'
import createBlog from './components/createBlog.vue'

const listingItems = ref(true);

function togglePage() {
  listingItems.value = !listingItems.value;
}

</script>

<template>
  <div class="min-h-screen bg-gradient-to-b from-gray-50 to-gray-100">

    <nav class="bg-indigo-600 shadow-lg">
      <div class="max-w-7xl mx-auto">
        <div class="flex justify-between items-center">
          <div class="flex space-x-1">
            <button class="p-4 font-medium text-white rounded-t-lg transition-all duration-200"
              :class="{ 'bg-indigo-800 shadow-inner': listingItems }" @click="togglePage">
              <span class="flex items-center gap-2">
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                    d="M4 6h16M4 10h16M4 14h16M4 18h16" />
                </svg>
                List
              </span>
            </button>
            <button class="p-4 font-medium text-white rounded-t-lg transition-all duration-200"
              :class="{ 'bg-indigo-800 shadow-inner': !listingItems }" @click="togglePage">
              <span class="flex items-center gap-2">
                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4" />
                </svg>
                Create
              </span>
            </button>
          </div>
        </div>
      </div>
    </nav>

    <main class="py-8">
      <div class="max-w-4xl mx-auto px-4">
        <div class="bg-white rounded-lg shadow-lg p-6">
          <listBlogs v-if="listingItems" />
          <createBlog v-else />
        </div>
      </div>
    </main>
  </div>
</template>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
