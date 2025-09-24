<template>
    <div class="pt-32 px-4 w-full max-w-2xl mx-auto flex-1 pb-20">
        <h1 class="text-3xl font-semibold mb-8 text-left">Thoughts, Writing & Code</h1>
        <div class="flex flex-col gap-2  opacity: 0.7;">
            <NuxtLink v-for="post in posts" :key="post.path" :to="post.path"
                class="block group text-left py-4  transition">
                <h2 class="!text-2xl mb-1 group-hover:text-neutral-800 text-neutral-700">{{ post.title }}</h2>
                <p class="text-neutral-500 text-sm mb-0">{{ post.description }}</p>
            </NuxtLink>
        </div>
    </div>
</template>

<script setup lang="ts">
const { data: posts } = await useAsyncData('posts-list', () => {
    return queryCollection('posts')
        .order('date', 'DESC')
        .select('title', 'path', 'description')
        .all()
})
</script>