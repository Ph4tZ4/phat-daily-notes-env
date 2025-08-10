<template>
  <div class="flex justify-center items-center min-h-[70vh]">
    <div class="card w-full max-w-sm">
      <h1 class="text-2xl font-bold text-center text-pink-300">Create account</h1>
      <p class="text-xs text-center text-pink-200/60 mt-1">Join DailyNotes</p>

      <div class="mt-4 space-y-3">
        <input v-model="username" placeholder="Username" class="input" />
        <input v-model="password" type="password" placeholder="Password" class="input" />
      </div>

      <button @click="handleRegister" class="btn-primary w-full mt-4">Sign up</button>

      <p v-if="errorMsg" class="text-red-400 text-sm mt-3 text-center">
        {{ errorMsg }}
      </p>

      <p class="text-xs text-center mt-4 text-pink-200/70">
        Already have an account?
        <NuxtLink class="underline hover:text-pink-200" to="/login">Login</NuxtLink>
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

const handleRegister = async () => {
  errorMsg.value = ''
  try {
    await axios.post(`${apiUrl}/api/register`, {
      username: username.value,
      password: password.value
    })
    router.push('/login')
  } catch (err) {
    errorMsg.value = err.response?.data?.msg || 'Registration failed.'
  }
}
</script>