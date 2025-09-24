<script setup lang="ts">
const route = useRoute()
const { data: page } = await useAsyncData(route.path, () => {
    return queryCollection('posts').path(route.path).first()
})
</script>

<template>
    <div class="pt-32 px-4 w-full max-w-2xl mx-auto min-h-screen">
        <h1 class="text-3xl font-semibold mb-8 text-left">{{ page?.title }}</h1>
        <div class="prose prose-neutral text-left max-w-none mb-12">
            <ContentRenderer v-if="page" :value="page" />
        </div>
        <div class="py-8 border-t-stone-500/50 border-t">
            <NuxtLink to="/posts" class="inline-flex items-center text-neutral-500 hover:text-neutral-800 text-sm">
                <UIcon name="i-mdi-arrow-left" class="mr-2 w-4 h-4" /> Back
            </NuxtLink>
        </div>
    </div>
</template>