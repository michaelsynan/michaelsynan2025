<script
  setup
  lang="ts"
>
const route = useRoute()
const { data: page } = await useAsyncData(route.path, () => {
  return queryCollection('posts').path(route.path).first()
})
</script>

<template>
  <div class="flex flex-col min-h-screen px-4 w-full max-w-2xl mx-auto">
    <div class="flex-1 pt-32">
      <h1 class="text-3xl font-semibold mb-8 text-left">{{ page?.title }}</h1>
      <div class="prose prose-neutral text-left max-w-none mb-12">
        <ContentRenderer
          v-if="page"
          :value="page"
          class="prose"
        />
      </div>
      <div class="py-8 border-t-stone-500/50 border-t">
        <NuxtLink
          to="/posts"
          class="inline-flex items-center text-muted hover:text-default text-sm"
        >
          <UIcon
            name="i-mdi-arrow-left"
            class="mr-2 w-4 h-4"
          /> Back
        </NuxtLink>
      </div>
    </div>

  </div>
</template>