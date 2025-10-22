<template>
  <div class="pt-32 px-4 w-full max-w-2xl mx-auto flex-1 pb-20">

    <h1 class="text-3xl font-semibold mb-8 text-left">Thoughts, Writing & Code</h1>
    <div class="flex flex-col gap-2">
      <NuxtLink
        v-for="post in posts || []"
        :key="post.path"
        :to="post.path"
        class="block text-left py-4"
      >
        <h2 class="!text-2xl mb-1">{{ post.title }}</h2>
        <p class="text-muted text-sm mb-0">{{ post.description }}</p>
      </NuxtLink>
    </div>
    <details
      class="mt-12 border-t border-stone-500 pt-8"
      v-if="archivedPosts && archivedPosts.length > 0"
    >
      <summary class="cursor-pointer text-base py-2 px-2 font-medium">
        Show Archived Posts
      </summary>
      <div class="flex flex-col gap-2 mt-2">
        <NuxtLink
          v-for="post in archivedPosts || []"
          :key="post.path"
          :to="post.path"
          class="block text-left py-4 opacity-70 hover:opacity-100 border-b last:border-b-0"
        >
          <h2 class="!text-2xl mb-1">{{ post.title }}</h2>
          <p class="text-muted text-sm mb-0">{{ post.description }}</p>
        </NuxtLink>
      </div>
    </details>
  </div>
</template>

<script
  setup
  lang="ts"
>
const { data: posts } = await useAsyncData('posts-list', () => {
  return queryCollection('posts')
    .where('archived', '<>', true)
    .order('date', 'DESC')
    .select('title', 'path', 'description', 'archived')
    .all()
})
const { data: archivedPosts } = await useAsyncData('archived-posts-list', () => {
  return queryCollection('posts')
    .where('archived', '=', true)
    .order('date', 'DESC')
    .select('title', 'path', 'description', 'archived')
    .all()
})
</script>