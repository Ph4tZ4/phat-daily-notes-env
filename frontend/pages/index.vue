<template>
  <section>
    <div class="text-center mb-10">
      <h1 class="text-4xl md:text-5xl font-extrabold tracking-tight text-pink-300">DailyNotes</h1>
      <p class="mt-3 text-pink-200/80 max-w-2xl mx-auto">
        A minimal weblog for your daily thoughts. Capture, organize, and revisit your notes with a sleek black and pink aesthetic.
      </p>
      <div class="mt-6 flex items-center justify-center gap-3">
        <NuxtLink to="/dashboard" class="btn-primary">Go to Dashboard</NuxtLink>
        <NuxtLink to="/login" class="btn-outline">Login</NuxtLink>
      </div>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
      <div class="card">
        <h3 class="text-pink-300 font-semibold mb-1">Write daily</h3>
        <p class="text-pink-100/80 text-sm">Capture ideas quickly with a simple flow.</p>
      </div>
      <div class="card">
        <h3 class="text-pink-300 font-semibold mb-1">Organized layout</h3>
        <p class="text-pink-100/80 text-sm">A clean weblog style with readable typography.</p>
      </div>
      <div class="card">
        <h3 class="text-pink-300 font-semibold mb-1">Private by default</h3>
        <p class="text-pink-100/80 text-sm">Your notes live in your account, not public.</p>
      </div>
    </div>
  </section>
</template>
