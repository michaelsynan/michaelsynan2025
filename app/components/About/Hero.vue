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
  <div class="flex flex-col justify-between items-start min-h-screen p-4 gap-8 md:gap-0">
    <div class="grid grid-cols-1 md:grid-cols-2 w-full flex-1 min-h-1/2">
      <div class="hidden md:block" />
      <div class="flex flex-col justify-center h-full pt-20 md:pt-0">
        <h1 class="text-3xl md:text-5xl mx-auto max-w-md leading-tight text-left">Hi, I'm Michael Synan. Pleased to meet
          you.
        </h1>
      </div>
    </div>
    <div class="flex flex-col md:flex-row w-full h-auto md:h-[600px] gap-8 md:gap-10">
      <div class="flex-1 flex h-full overflow-hidden">
        <NuxtImg src="/michael_synan.webp" alt="Michael Synan" class="object-cover h-full w-full" />
      </div>
      <div class="flex-[3] flex flex-col w-full">
        <div id="home-content-wrapper"
          class="h-full flex items-start justify-start max-w-xl gap-4 overflow-hidden flex-col">
          <!-- <Transition name="fade-tab" mode="out-in">
            <component :is="selectedTabComponent" />
          </Transition> -->
          <p>
            I'm Michael, I help create meaningful online experiences from the ground up—design to code. I'm a long-time
            Linux user, philosophy nerd, and open-source advocate. My Master’s degree in Urban Affairs and Bachelor’s
            degree in Psychology inform my approach to understanding the human side of technology.
          </p>
          <p>
            I'm the founder of <nuxt-link to="https://formworkstudios.com" target="_blank"
              class="underline-thick">Formwork
              Studios</nuxt-link>.
          </p>
          <div class="w-full h-full" />
          <div class="w-full">
          </div>
        </div>
        <SharedSocials class="ml-auto" />


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
