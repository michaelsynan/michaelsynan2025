<template>
    <div class="pt-32 px-4 w-full max-w-2xl mx-auto min-h-screen">
        <h1 class="text-3xl font-semibold mb-8 text-left">Thoughts, Writing & Code</h1>
        <div class="flex flex-col gap-8">
            <NuxtLink v-for="post in posts" :key="post.path" :to="post.path"
                class="block group text-left py-4 border-b border-neutral-200 hover:bg-neutral-50 transition">
                <h2 class="text-xl mb-1 group-hover:text-neutral-800 text-neutral-700">{{ post.title }}</h2>
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