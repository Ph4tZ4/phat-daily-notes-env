<template>
  <div class="flex justify-center items-center min-h-screen bg-gray-100">
    <div class="bg-white p-6 rounded shadow w-80">
      <h1 class="text-xl font-bold mb-2 text-center">Login</h1>

      <!-- Show API URL -->
      <p class="text-sm text-gray-500 text-center mb-2">
        API URL: {{ apiUrl }}
      </p>

      <input
        v-model="username"
        placeholder="Username"
        class="mb-3 p-2 border w-full rounded"
      />

      <input
        v-model="password"
        type="password"
        placeholder="Password"
        class="mb-4 p-2 border w-full rounded"
      />

      <button
        @click="handleLogin"
        class="bg-blue-500 text-white p-2 w-full rounded hover:bg-blue-600"
      >
        Login
      </button>

      <p v-if="errorMsg" class="text-red-500 text-sm mt-3 text-center">
        {{ errorMsg }}
      </p>
    </div>
  </div>
</template>

<script setup>
import axios from 'axios'
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const username = ref('')
const password = ref('')
const errorMsg = ref('')
const apiUrl = import.meta.env.VITE_API_URL
const router = useRouter()

const handleLogin = async () => {
  errorMsg.value = ''
  try {
    const res = await axios.post(`${apiUrl}/api/login`, {
      username: username.value,
      password: password.value
    })
    localStorage.setItem('token', res.data.access_token)
    console.log('Token:', res.data.access_token)
    router.push('/dashboard')
  } catch (err) {
    errorMsg.value =
      err.response?.data?.msg || 'Login failed. Please try again.'
  }
}
</script>
