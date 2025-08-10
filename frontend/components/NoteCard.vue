<template>
  <article class="card mb-4">
    <header class="flex items-baseline justify-between mb-2">
      <h2 class="font-semibold text-pink-300 text-lg">{{ note.title }}</h2>
      <time class="text-xs text-pink-400/70">{{ note.created_at }}</time>
    </header>
    <p class="text-sm text-pink-100/90 whitespace-pre-line">{{ note.content }}</p>
    <div class="mt-3 flex justify-end">
      <button @click="$emit('delete', note.id)" class="btn-outline text-sm">Delete</button>
    </div>
  </article>
</template>

<script setup>
defineProps({ note: Object })
defineEmits(['delete'])
</script>
