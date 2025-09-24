<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue';
import { useRouter } from 'vue-router';
const showMenu = ref(false);
const menuRef = ref(null);
const router = useRouter();

function handleClickOutside(event) {
  if (showMenu.value && menuRef.value && !menuRef.value.contains(event.target)) {
    showMenu.value = false;
  }
}

onMounted(() => {
  document.addEventListener('mousedown', handleClickOutside);
  router.afterEach(() => {
    showMenu.value = false;
  });
});
onBeforeUnmount(() => {
  document.removeEventListener('mousedown', handleClickOutside);
});
</script>

<template>
  <nav class="flex flex-row justify-between items-center px-4 py-3 bg-transparent shadow-none fixed w-full top-0 z-50 ">
    <div class="flex items-center">
      <NuxtLink to="/">
        <NuxtImg src="/ms-logo.png" alt="Logo" width="40" height="40" class="block" />
      </NuxtLink>
    </div>
    <div class="flex items-center relative">
      <UButton color="neutral" variant="ghost" class="cursor-pointer"
        :class="['flex items-center justify-center p-0 w-10 h-10 border border-neutral-900 rounded-none', showMenu ? 'bg-[#fdfaea]' : 'bg-[#fdfaea]']"
        @click="showMenu = !showMenu"
        @mouseover="(e: MouseEvent) => (e.currentTarget as HTMLElement).style.backgroundColor = 'white'"
        @mouseleave="(e: MouseEvent) => (e.currentTarget as HTMLElement).style.backgroundColor = '#fdfaea'">
        <svg v-if="!showMenu" width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="11" y="4" width="2" height="16" rx="1" fill="currentColor" />
          <rect x="4" y="11" width="16" height="2" rx="1" fill="currentColor" />
        </svg>
        <svg v-else width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="4" y="11" width="16" height="2" rx="1" fill="currentColor" />
        </svg>
      </UButton>
      <Transition name="slide-menu">
        <div v-if="showMenu" ref="menuRef"
          class="absolute left-0 flex flex-row bg-[#fdfaea] border border-neutral-900 z-50 gap-10 transition-all duration-300 slide-menu-content hidden md:flex"
          style="height: 40px; min-width: 400px; top: 50%; transform: translate(calc(-100% - 16px), -50%) scaleX(1); transform-origin: right;">
          <NuxtLink to="/" class="flex items-center h-full px-4 hover:bg-white transition text-sm font-mono">Home
          </NuxtLink>
          <NuxtLink to="/about" class="flex items-center h-full px-4 hover:bg-white transition text-sm font-mono">About
          </NuxtLink>
          <NuxtLink to="/posts" class="flex items-center h-full px-4 hover:bg-white transition text-sm font-mono">
            Writing</NuxtLink>
          <NuxtLink to="/projects" class="flex items-center h-full px-4 hover:bg-white transition text-sm font-mono">
            Projects</NuxtLink>
          <NuxtLink to="/contact" class="flex items-center h-full px-4 hover:bg-white transition text-sm font-mono">
            Contact</NuxtLink>
        </div>
      </Transition>
      <!-- Mobile menu -->
      <Transition name="slide-menu">
        <div v-if="showMenu"
          class="fixed left-0 mx-4 right-0 top-[62px] w-auto  h-auto flex flex-col bg-[#fdfaea] border border-neutral-900 z-50 gap-0 md:hidden slide-menu-mobile transition-all duration-300"
          style="border-radius: 0;">

          <NuxtLink to="/" class="flex items-center h-14 px-4 hover:bg-white transition text-base font-mono">Home
          </NuxtLink>
          <NuxtLink to="/about" class="flex items-center h-14 px-4 hover:bg-white transition text-base font-mono">About
          </NuxtLink>
          <NuxtLink to="/posts" class="flex items-center h-14 px-4 hover:bg-white transition text-base font-mono">
            Writing</NuxtLink>
          <NuxtLink to="/projects" class="flex items-center h-14 px-4 hover:bg-white transition text-base font-mono">
            Projects</NuxtLink>
          <NuxtLink to="/contact" class="flex items-center h-14 px-4 hover:bg-white transition text-base font-mono">
            Contact</NuxtLink>
        </div>
      </Transition>
    </div>
  </nav>
</template>

<style scoped>
.slide-menu-enter-active {
  transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
}

.slide-menu-enter-from {
  transform: translateX(100%) scaleX(0);
  opacity: 0;
}

.slide-menu-enter-to {
  transform: translateX(0) scaleX(1);
  opacity: 1;
}

.slide-menu-leave-active {
  transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
}

.slide-menu-leave-from {
  transform: translateX(0) scaleX(1);
  opacity: 1;
}

.slide-menu-leave-to {
  transform: translateX(100%) scaleX(0);
  opacity: 0;
}
</style>
