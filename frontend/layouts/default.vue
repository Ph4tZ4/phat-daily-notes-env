<template>
  <div class="flex min-h-screen flex-col">
    <Navbar />
    <main class="flex-1">
      <div class="max-w-5xl mx-auto px-4 py-8">
        <slot />
      </div>
    </main>
    <Footer />
  </div>
  
</template>

<script setup>
import Navbar from '~/components/Navbar.vue'
import Footer from '~/components/Footer.vue'
</script>
