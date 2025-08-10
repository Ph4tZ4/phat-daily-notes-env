<template>
  <div>
    <div class="mb-6">
      <h1 class="text-3xl font-bold text-pink-300">My Notes</h1>
      <p class="text-sm text-pink-200/70">Your private weblog entries</p>
    </div>

    <div class="card mb-6">
      <div class="grid grid-cols-1 md:grid-cols-5 gap-3">
        <input v-model="title" placeholder="Title" class="input md:col-span-2" />
        <input v-model="content" placeholder="Write a quick note..." class="input md:col-span-3" />
      </div>
      <div class="mt-3 flex justify-end">
        <button @click="createNote" class="btn-primary">Publish</button>
      </div>
    </div>

    <div>
      <NoteCard
        v-for="note in notes"
        :key="note.id"
        :note="note"
        @delete="deleteNote"
      />
      <p v-if="notes.length === 0" class="text-pink-200/60 text-sm">No notes yet. Start your first post above.</p>
    </div>
  </div>
</template>

<script setup>
import axios from 'axios'
import { ref, onMounted } from 'vue'
import NoteCard from '@/components/NoteCard.vue' // หากยังไม่ได้ import

const API_URL = import.meta.env.VITE_API_URL

const title = ref('')
const content = ref('')
const notes = ref([])

const fetchNotes = async () => {
  const token = localStorage.getItem('token')
  const res = await axios.get(`${API_URL}/api/notes`, {
    headers: {
      Authorization: `Bearer ${token}`
    }
  })
  notes.value = res.data
}

const createNote = async () => {
  const token = localStorage.getItem('token')
  try {
    await axios.post(`${API_URL}/api/notes`, {
      title: title.value,
      content: content.value
    }, {
      headers: {
        Authorization: `Bearer ${token}`
      }
    })
    title.value = ''
    content.value = ''
    fetchNotes()
  } catch (e) {
    console.error('Create note failed:', e)
  }
}

const deleteNote = async (id) => {
  const token = localStorage.getItem('token')
  await axios.delete(`${API_URL}/api/notes/${id}`, {
    headers: {
      Authorization: `Bearer ${token}`
    }
  })
  fetchNotes()
}

onMounted(fetchNotes)
</script>
