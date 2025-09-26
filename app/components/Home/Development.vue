<script setup lang="ts">
import { ref } from 'vue';
const selectedTab = ref('A');
</script>

<template>
  <div class="flex flex-row w-full h-[500px]">
    <div class="flex flex-col items-start justify-between py-8 pr-8 border-r border-neutral-200 h-full max-w-max">
      <!-- side menu area -->
      <nav class="flex flex-col gap-6 w-full items-start text-left">
        <button
          class="text-sm transition flex items-center cursor-pointer bg-transparent border-none p-0 focus:outline-none"
          :class="selectedTab === 'A' ? 'text-neutral-900' : 'text-neutral-700'" @click="selectedTab = 'A'">
          <span class="font-mono mr-1">A.</span>
          <span class="ml-1 cursor-pointer">Vue/Nuxt</span>
        </button>
        <button
          class="text-sm transition flex items-center cursor-pointer bg-transparent border-none p-0 focus:outline-none"
          :class="selectedTab === 'B' ? 'text-neutral-900' : 'text-neutral-700'" @click="selectedTab = 'B'">
          <span class="font-mono mr-1">B.</span>
          <span class="ml-1 cursor-pointer">Shopify</span>
        </button>
        <button
          class="text-sm transition flex items-center cursor-pointer bg-transparent border-none p-0 focus:outline-none"
          :class="selectedTab === 'C' ? 'text-neutral-900' : 'text-neutral-700'" @click="selectedTab = 'C'">
          <span class="font-mono mr-1">C.</span>
          <span class="ml-1 cursor-pointer">WordPress</span>
        </button>
        <button
          class="text-sm transition flex items-center cursor-pointer bg-transparent border-none p-0 focus:outline-none"
          :class="selectedTab === 'D' ? 'text-neutral-900' : 'text-neutral-700'" @click="selectedTab = 'D'">
          <span class="font-mono mr-1">D.</span>
          <span class="ml-1 flex-1 cursor-pointer">GitHub</span>
          <UIcon name="i-mdi-arrow-top-right" class="inline-block ml-1.5 w-4 h-4" />
        </button>
      </nav>
    </div>
    <div class="flex flex-col items-start justify-start h-full w-full p-8">
      <Transition name="fade-content" mode="out-in">
        <div :key="selectedTab" class="w-full text-left">
          <div v-if="selectedTab === 'A'">
            <h2 class="text-xl mb-2">Vue & Nuxt</h2>
            <p class="text-neutral-500 max-w-2xl">
              I primarily build modern web applications using Vue and Nuxt, leveraging Nuxt Content and Nuxt UI while
              following SPA and SSR best practices. Projects are typically deployed on Vercel and Cloudflare, though I’m
              equally comfortable hosting servers on DigitalOcean or AWS, with Supabase handling backend services. This
              stack enables fast, scalable applications and is simply enjoyable to work with.
            </p>
          </div>
          <div v-else-if="selectedTab === 'B'">
            <h2 class="text-xl mb-2">Shopify</h2>
            <p class="text-neutral-500 max-w-2xl">Shopify is the most widely used eCommerce platform for small
              businesses and brands, with the highest-converting checkout on the internet. I set up your Shopify store,
              email flows, abandoned cart recovery, custom theme development, deals, bundling, and CRM integration.
              Shopify development for eCommerce solutions and custom storefronts.

            </p>
          </div>
          <div v-else-if="selectedTab === 'C'">
            <h2 class="text-xl 
            mb-2">WordPress</h2>
            <p class="text-neutral-500 max-w-2xl">I've been buidling and hosting WordPress sites for 15 years. From
              custom theme and plugin development to automation and marketing.</p>
          </div>
          <div v-else-if="selectedTab === 'D'">
            <h2 class="text-xl font-semibold mb-2">GitHub</h2>
            <p class="text-neutral-500 max-w-2xl">Find my open source work and code repositories on GitHub.</p>
          </div>
        </div>
      </Transition>
    </div>
  </div>
</template>

<style scoped>
.fade-content-enter-active,
.fade-content-leave-active {
  transition: opacity 0.25s cubic-bezier(0.4, 0, 0.2, 1);
}

.fade-content-enter-from,
.fade-content-leave-to {
  opacity: 0;
}

.fade-content-enter-to,
.fade-content-leave-from {
  opacity: 1;
}
</style>
