<script setup>
import Swal from 'sweetalert2'
import { ref } from 'vue'

const title = ref('')
const author = ref('')
const content = ref('')

async function submit() {
  try {
    const res = await fetch(`http://localhost:8080/articles`, {
      method: "POST",
      headers: {
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        title: title.value,
        authorName: author.value,
        content: content.value
      })
    })

    if (!res.ok) throw new Error('Error saving article')

    await Swal.fire({
      title: "Success",
      text: "Article created successfully!",
      icon: "success"
    })

    title.value = ''
    author.value = ''
    content.value = ''

  } catch (error) {
    await Swal.fire({
      title: "Error",
      text: "Article could not be created!",
      icon: "error"
    })
  }
}

</script>

<template>
  <div class="bg-white shadow-md rounded-md w-full p-6">
    <h1 class="text-center text-2xl font-semibold py-2 mb-6">Create Article</h1>

    <form @submit.prevent="submit" class="max-w-lg mx-auto">
      <div class="mb-4">
        <label for="title" class="block py-2">Title</label>
        <input v-model="title" id="title" type="text"
          class="w-full shadow appearance-none border border-indigo-200 rounded py-2 px-3 text-black"
          placeholder="Title">
      </div>

      <div class="mb-4">
        <label for="author" class="block py-2">Author</label>
        <input v-model="author" id="author" type="text"
          class="w-full shadow appearance-none border border-indigo-200 rounded py-2 px-3 text-black"
          placeholder="Author name">
      </div>

      <div class="mb-4">
        <label for="content" class="block py-2">Content</label>
        <textarea v-model="content" id="content" type="textarea" rows="20"
          class="w-full shadow appearance-none border border-indigo-200 rounded py-2 px-3 text-black"
          placeholder="Enter article content"></textarea>
      </div>

      <div class="flex gap-2 my-2 justify-center">
        <button type="button" id="cancelButton"
          class="py-4 px-2 rounded-md shadow bg-red-500 hover:bg-red-600 text-white transition-colors">Cancel</button>
        <button type="submit" id="submitButton"
          class="py-4 px-2 rounded-md shadow bg-blue-500 hover:bg-blue-600 text-white transition-colors">Save</button>
      </div>
    </form>

  </div>
</template>
