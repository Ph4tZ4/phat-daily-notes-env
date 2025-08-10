<template>
  <nav class="sticky top-0 z-50 border-b border-pink-900/60 bg-black/80 backdrop-blur">
    <div class="max-w-5xl mx-auto px-4 py-4 flex items-center justify-between">
      <NuxtLink to="/" class="flex items-center gap-2 no-underline">
        <span class="inline-block h-3 w-3 rounded-full bg-pink-600"></span>
        <span class="font-bold text-pink-300 text-xl tracking-wide">DailyNotes</span>
      </NuxtLink>
      <div class="flex items-center gap-3">
        <NuxtLink to="/" class="text-pink-200 hover:text-pink-100 no-underline">Home</NuxtLink>
        <NuxtLink to="/dashboard" class="text-pink-200 hover:text-pink-100 no-underline">Dashboard</NuxtLink>
        <NuxtLink to="/login" class="btn-outline">Login</NuxtLink>
      </div>
    </div>
  </nav>
  
</template>
