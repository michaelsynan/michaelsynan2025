<script setup lang="ts">
const { data: posts } = await useAsyncData('posts-list', () => {
  return queryCollection('posts')
    .order('date', 'DESC')
    .select('title', 'path', 'description')
    .all()
})
const hoveredIndex = ref(-1);
</script>

<template>
  <div class="pt-4 pb-12 px-4 w-full max-w-2xl mr-auto">
    <h2 class="text-2xl font-semibold mb-3 text-left">Blog Posts</h2>
    <div class="flex flex-col">
      <div v-for="(post, i) in posts.slice(0, 2)" :key="post.path" class="group pb-3" @mouseenter="hoveredIndex = i"
        @mouseleave="hoveredIndex = -1">
        <NuxtLink :to="post.path" class="block text-left py-2 transition">
          <h3 :class="[
            'text-lg mb-1 transition-opacity duration-250',
            hoveredIndex === -1 || hoveredIndex === i ? 'text-neutral-700 opacity-100' : 'text-neutral-400 opacity-60'
          ]">
            {{ post.title }}
          </h3>
          <p :class="[
            'text-neutral-500 text-sm mb-0 transition-opacity duration-250',
            hoveredIndex === -1 || hoveredIndex === i ? 'opacity-100' : 'text-neutral-400 opacity-60'
          ]">
            {{ post.description }}
          </p>
        </NuxtLink>
      </div>
      <NuxtLink to="/posts" class="mt-4 flex items-center text-sm text-neutral-500 hover:text-neutral-800 transition">
        Read all posts
        <UIcon name="i-mdi-arrow-right" class="ml-1 w-4 h-4" />
      </NuxtLink>
    </div>
  </div>
</template>

<style scoped>
/* For smooth opacity transitions on hover */
.transition-opacity {
  transition: opacity 0.25s cubic-bezier(0.4, 0, 0.2, 1);
}
</style>
