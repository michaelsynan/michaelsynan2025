<script setup lang="ts">
import { ref } from 'vue';
const selectedTab = ref('Design');
</script>

<template>
  <div class="flex flex-col justify-between items-start min-h-screen p-4">
    <div class="grid grid-cols-2 w-full flex-1 min-h-1/2">
      <div />
      <div class="flex flex-col justify-center h-full">
        <h1 class="text-5xl mx-auto max-w-md leading-tight text-left">Building Nice Things for Human Beings.
        </h1>
      </div>
    </div>
    <div class="flex flex-row w-full h-1/2 max-h-1/2 gap-20">
      <div class="flex-1 flex items-end">
        <NuxtImg src="/michael_synan.webp" alt="Michael Synan" height="600" class="object-cover" />
      </div>
      <div class="flex-[3] flex flex-col w-full">
        <div id="home-content-wrapper"
          class="h-full flex items-center justify-center border-t border-neutral-300 pt-2 overflow-hidden">
          <div id="home-content" class="w-full text-center">
            <HomeDesign v-if="selectedTab === 'Design'" />
            <HomeDevelopment v-else-if="selectedTab === 'Development'" />
            <HomeWriting v-else-if="selectedTab === 'Writing'" />
          </div>
        </div>
        <div class="flex flex-row gap-20">
          <div class="flex-1 flex border-t pt-4 cursor-pointer justify-center"
            :class="selectedTab === 'Design' ? 'border-neutral-800 text-neutral-800' : 'border-neutral-300 text-neutral-400'"
            @click="selectedTab = 'Design'">
            <div class="w-full text-left flex items-center gap-2">
              <span class="font-mono">01.</span> Design
            </div>
          </div>
          <div class="flex-1 flex border-t pt-4 cursor-pointer justify-center"
            :class="selectedTab === 'Development' ? 'border-neutral-800 text-neutral-800' : 'border-neutral-300 text-neutral-400'"
            @click="selectedTab = 'Development'">
            <div class="w-full text-left flex items-center gap-2">
              <span class="font-mono">02.</span> Development
            </div>
          </div>
          <div class="flex-1 flex border-t pt-4 cursor-pointer justify-center"
            :class="selectedTab === 'Writing' ? 'border-neutral-800 text-neutral-800' : 'border-neutral-300 text-neutral-400'"
            @click="selectedTab = 'Writing'">
            <div class="w-full text-left flex items-center gap-2">
              <span class="font-mono">03.</span> Writing
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
