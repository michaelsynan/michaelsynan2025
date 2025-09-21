  <script setup lang="ts">
  import { ref } from 'vue';
  const showMenu = ref(false);
</script>

<template>
  <nav class="flex flex-row justify-between items-center px-4 py-3 bg-transparent shadow-none fixed w-full top-0 z-50 ">
    <div class="flex items-center">
      <NuxtImg src="/ms-logo.png" alt="Logo" width="40" height="40" class="block" />
    </div>
    <div class="flex items-center relative">
      <UButton color="neutral" variant="ghost"
        :class="['flex items-center justify-center p-0 w-10 h-10 border border-neutral-900 rounded-none', showMenu ? 'bg-[#fdfaea]' : 'bg-[#fdfaea]']"
        @click="showMenu = !showMenu">
        <svg v-if="!showMenu" width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="11" y="4" width="2" height="16" rx="1" fill="currentColor" />
          <rect x="4" y="11" width="16" height="2" rx="1" fill="currentColor" />
        </svg>
        <svg v-else width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="4" y="11" width="16" height="2" rx="1" fill="currentColor" />
        </svg>
      </UButton>
      <div v-if="showMenu"
        class="absolute right-0 top-full mt-2 w-40 bg-white border border-neutral-200 flex flex-col z-50">
        <a href="#" class="px-4 py-2 hover:bg-neutral-100">Home</a>
        <a href="#" class="px-4 py-2 hover:bg-neutral-100">About</a>
        <a href="#" class="px-4 py-2 hover:bg-neutral-100">Contact</a>
      </div>
    </div>
  </nav>
</template>

<style scoped></style>
