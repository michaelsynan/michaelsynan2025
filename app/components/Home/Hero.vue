<script setup lang="ts">
import { ref, computed } from 'vue';
import HomeDesign from '../Home/Design.vue';
import HomeDevelopment from '../Home/Development.vue';
import HomeWriting from '../Home/Writing.vue';
const selectedTab = ref('Design');
const selectedTabComponent = computed(() => {
  if (selectedTab.value === 'Design') return HomeDesign;
  if (selectedTab.value === 'Development') return HomeDevelopment;
  if (selectedTab.value === 'Writing') return HomeWriting;
  return null;
});
</script>

<template>
  <div class="flex flex-col justify-between items-start min-h-screen p-0 md:p-4 gap-8 md:gap-0 w-full">
    <div class="grid grid-cols-1 md:grid-cols-2 w-full flex-1 min-h-screen md:min-h-1/2 p-4 md:p-0">
      <div class="hidden md:block" />
      <div class="flex flex-col justify-end md:justify-center h-full pt-0  mr-auto md:mr-[unset]">
        <div class="flex md:hidden h-full">
          <div id="some-stuff-content">Some stuff</div>
        </div>
        <NuxtImg src="/michael_synan.webp" alt="Michael Synan" class="object-cover w-1/2 flex md:hidden mb-4" />
        <h1 class="text-3xl md:text-5xl !ml-0 md:!ml-auto md:mx-auto max-w-md leading-tight text-left flex flex-col">
          <span>Building Nice
            Things</span><span>for Human
            Beings.</span>
        </h1>
        <div class="flex md:hidden pt-4 flex-row text-sm gap-2 max-h-content w-full justify-between">
          <div>DESIGN</div>
          <div>DEVELOPMENT</div>
          <div>WRITING</div>
        </div>
      </div>
    </div>
    <div class="flex flex-col md:flex-row w-full h-auto md:h-[600px] gap-8 md:gap-10">
      <!-- home image -->
      <div class="flex-1 hidden md:flex h-full overflow-hidden">
        <NuxtImg src="/michael_synan.webp" alt="Michael Synan" class="object-cover h-full w-full" />
      </div>
      <!-- right side -->
      <!-- right side desktop -->
      <div class="flex-[3] hidden md:flex flex-col w-full">
        <div id="home-content-wrapper"
          class="h-full flex items-start justify-center border-t border-neutral-300 pt py-2 overflow-hidden">
          <Transition name="fade-tab" mode="out-in">
            <component :is="selectedTabComponent" />
          </Transition>
        </div>
        <div class="flex flex-row gap-20">
          <div class="flex-1 flex border-t pt-4 cursor-pointer"
            :class="selectedTab === 'Design' ? 'border-neutral-800 text-neutral-800' : 'border-neutral-300 text-neutral-400'"
            @click="selectedTab = 'Design'">
            <div class="w-full flex items-center gap-2 justify-between">
              <div class="flex items-center gap-2 text-left">
                <span class="font-mono">01.</span> Design
              </div>
              <template v-if="selectedTab === 'Design'">
                <NuxtLink to="/projects"
                  class="flex items-center text-xs text-neutral-500 hover:text-neutral-800 rounded transition-colors duration-150">
                  View Projects
                  <UIcon name="i-mdi-arrow-right" class="ml-1 w-4 h-4" />
                </NuxtLink>
              </template>
            </div>
          </div>
          <div class="flex-1 flex border-t pt-4 cursor-pointer"
            :class="selectedTab === 'Development' ? 'border-neutral-800 text-neutral-800' : 'border-neutral-300 text-neutral-400'"
            @click="selectedTab = 'Development'">
            <div class="w-full flex items-center gap-2 justify-between">
              <div class="flex items-center gap-2 text-left">
                <span class="font-mono">02.</span> Development
              </div>
              <template v-if="selectedTab === 'Development'">
                <NuxtLink to="/projects"
                  class="flex items-center text-xs text-neutral-500 hover:text-neutral-800 rounded transition-colors duration-150">
                  View Projects
                  <UIcon name="i-mdi-arrow-right" class="ml-1 w-4 h-4" />
                </NuxtLink>
              </template>
            </div>
          </div>
          <div class="flex-1 flex border-t pt-4 cursor-pointer"
            :class="selectedTab === 'Writing' ? 'border-neutral-800 text-neutral-800' : 'border-neutral-300 text-neutral-400'"
            @click="selectedTab = 'Writing'">
            <div class="w-full flex items-center gap-2 justify-between">
              <div class="flex items-center gap-2 text-left">
                <span class="font-mono">03.</span> Writing
              </div>
              <template v-if="selectedTab === 'Writing'">
                <NuxtLink to="/posts"
                  class="flex items-center text-xs text-neutral-500 hover:text-neutral-800 rounded transition-colors duration-150">
                  View Writing
                  <UIcon name="i-mdi-arrow-right" class="ml-1 w-4 h-4" />
                </NuxtLink>
              </template>
            </div>
          </div>
        </div>
      </div>

      <!-- right side mobile -->
      <div class="flex-[3] flex flex-col md:hidden w-full">
        <div></div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.fade-tab-enter-active,
.fade-tab-leave-active {
  transition: opacity 0.25s cubic-bezier(0.4, 0, 0.2, 1);
}

.fade-tab-enter-from,
.fade-tab-leave-to {
  opacity: 0;
}

.fade-tab-enter-to,
.fade-tab-leave-from {
  opacity: 1;
}
</style>
