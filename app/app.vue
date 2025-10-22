<template>
  <UApp class="min-h-screen flex flex-col">
    <div class="flex-1 flex flex-col">
      <SharedNav />
      <NuxtRouteAnnouncer />
      <Transition
        name="fade"
        mode="out-in"
      >
        <NuxtPage />
      </Transition>
    </div>
    <template v-if="route.path !== '/' && route.path !== '/about'">
      <SharedFooter class="bottom-0" />
    </template>
  </UApp>

</template>

<script setup>
import { useRoute } from 'vue-router';
const route = useRoute();
// No imports needed, Nuxt auto-imports components in Shared/
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.25s cubic-bezier(0.4, 0, 0.2, 1);
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-to,
.fade-leave-from {
  opacity: 1;
}
</style>
