<script setup lang="ts"></script>

<template>
  <div class="grid grid-cols-4 h-[500px] w-full">
    <div
      class="col-span-1 flex flex-col items-start justify-between py-8 pr-8 border-r border-neutral-200 h-full max-w-max">
      <nav class="flex flex-col gap-6 w-full items-start ">
        <button class="text-lg text-neutral-700 hover:text-neutral-900 transition">Nuxt/Vue</button>
        <button class="text-lg text-neutral-700 hover:text-neutral-900 transition">Shopify</button>
        <button class="text-lg text-neutral-700 hover:text-neutral-900 transition">WordPress</button>
      </nav>
      <a href="https://github.com/yourgithub" target="_blank"
        class="text-xs text-neutral-500 hover:text-neutral-800 mt-8">GitHub</a>
    </div>
    <div class="col-span-3 flex items-center justify-center h-full">
      <div class="text-neutral-400 text-xl">Placeholder centered content</div>
    </div>
  </div>
</template>

<style scoped></style>
