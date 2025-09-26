<script setup lang="ts">
const { data: posts } = await useAsyncData('posts-list', () => {
  return queryCollection('posts')
    .order('date', 'DESC')
    .select('title', 'path', 'description')
    .all()
})
// ...no hover state needed
</script>

<template>
  <div class="pt-4 pb-12 px-4 w-full max-w-2xl mr-auto">
    <h2 class="text-2xl font-semibold mb-3 text-left">Blog Posts</h2>
    <div class="flex flex-col">
      <div v-for="post in (posts || []).slice(0, 2)" :key="post.path" class="group pb-3">
        <NuxtLink :to="post.path" class="block text-left py-2">
          <h3 class="text-lg mb-1">{{ post.title }}</h3>
          <p class="text-neutral-500 text-sm mb-0">{{ post.description }}</p>
        </NuxtLink>
      </div>
      <NuxtLink to="/posts" class="mt-4 flex items-center text-sm text-neutral-500 hover:text-neutral-800 transition">
        Read all posts
        <UIcon name="i-mdi-arrow-right" class="ml-1 w-4 h-4" />
      </NuxtLink>
    </div>
  </div>
</template>
