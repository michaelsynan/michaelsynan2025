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
  // Also listen for touchstart so mobile taps outside close the menu correctly
  document.addEventListener('touchstart', handleClickOutside);
  router.afterEach(() => {
    showMenu.value = false;
  });
});
onBeforeUnmount(() => {
  document.removeEventListener('mousedown', handleClickOutside);
  document.removeEventListener('touchstart', handleClickOutside);
});
</script>

<template>
  <nav
    class="flex flex-row justify-between items-center px-4 py-3 bg-transparent shadow-none fixed w-full top-0 pointer-events-auto"
    style="z-index: 100000;">
    <div class="flex items-center">
      <NuxtLink to="/" style="position: relative; z-index: 100001;">
        <NuxtImg src="/ms-logo.png" alt="Logo" width="40" height="40" class="block" />
      </NuxtLink>
    </div>
    <div ref="menuRef" class="flex items-center relative">
      <UButton
        color="neutral"
        variant="ghost"
        class="cursor-pointer"
        style="position: relative; z-index: 100001;"
        :class="['flex items-center justify-center p-0 w-10 h-10 border border-neutral-900 rounded-none', showMenu ? 'bg-[#fdfaea]' : 'bg-[#fdfaea]']"
        @click="showMenu = !showMenu"
        @mouseover="(e: MouseEvent) => (e.currentTarget as HTMLElement).style.backgroundColor = 'white'"
        @mouseleave="(e: MouseEvent) => (e.currentTarget as HTMLElement).style.backgroundColor = '#fdfaea'"
      >
        <svg v-if="!showMenu" width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="11" y="4" width="2" height="16" rx="1" fill="currentColor" />
          <rect x="4" y="11" width="16" height="2" rx="1" fill="currentColor" />
        </svg>
        <svg v-else width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <rect x="4" y="11" width="16" height="2" rx="1" fill="currentColor" />
        </svg>
      </UButton>
      <Transition name="slide-menu">
        <div v-if="showMenu"
          class="absolute left-0 md:flex hidden flex-row bg-[#fdfaea] border border-neutral-900 z-50 gap-10 transition-all duration-300 slide-menu-content"
          style="height: 40px; min-width: 400px; top: 50%; transform: translate(calc(-100% - 16px), -50%) scaleX(1); transform-origin: right; pointer-events: auto; z-index: 60;">
          <NuxtLink to="/"
            class="flex items-center h-full px-4 hover:bg-white transition text-sm font-mono pointer-events-auto">Home
          </NuxtLink>
          <NuxtLink to="/about"
            class="flex items-center h-full px-4 hover:bg-white transition text-sm font-mono pointer-events-auto">About
          </NuxtLink>
          <NuxtLink to="/posts"
            class="flex items-center h-full px-4 hover:bg-white transition text-sm font-mono pointer-events-auto">
            Writing</NuxtLink>
          <NuxtLink to="/projects"
            class="flex items-center h-full px-4 hover:bg-white transition text-sm font-mono pointer-events-auto">
            Projects</NuxtLink>
          <NuxtLink to="/contact"
            class="flex items-center h-full px-4 hover:bg-white transition text-sm font-mono pointer-events-auto">
            Contact</NuxtLink>
        </div>
      </Transition>
      <!-- Mobile full-screen overlay menu (teleported to body so nav stays on top) -->
      <teleport to="body">
        <Transition name="slide-menu">
          <div
            v-if="showMenu"
            class="fixed inset-0 bg-[#fdfaea] md:hidden transition-all duration-300 slide-menu-mobile flex"
            style="border-radius: 0; pointer-events: auto; z-index: 10000;">

            <!-- Centered vertical links -->
            <div class="flex-1 h-full flex flex-col items-center justify-center">
              <nav class="w-full max-w-md px-6">
                <ul class="flex flex-col gap-6 items-start">
                  <li>
                    <NuxtLink
                      to="/"
                      class="text-2xl font-mono px-2 py-2 pointer-events-auto"
                      @click="showMenu = false"
                    >
                      Home
                    </NuxtLink>
                  </li>
                  <li>
                    <NuxtLink
                      to="/about"
                      class="text-2xl font-mono px-2 py-2 pointer-events-auto"
                      @click="showMenu = false"
                    >
                      About
                    </NuxtLink>
                  </li>
                  <li>
                    <NuxtLink
                      to="/posts"
                      class="text-2xl font-mono px-2 py-2 pointer-events-auto"
                      @click="showMenu = false"
                    >
                      Writing
                    </NuxtLink>
                  </li>
                  <li>
                    <NuxtLink
                      to="/projects"
                      class="text-2xl font-mono px-2 py-2 pointer-events-auto"
                      @click="showMenu = false"
                    >
                      Projects
                    </NuxtLink>
                  </li>
                  <li>
                    <NuxtLink
                      to="/contact"
                      class="text-2xl font-mono px-2 py-2 pointer-events-auto"
                      @click="showMenu = false"
                    >
                      Contact
                    </NuxtLink>
                  </li>
                </ul>
              </nav>
            </div>

          </div>
        </Transition>
      </teleport>
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
