<template>
  <div>
    <SharedNav />
    <NuxtRouteAnnouncer />
    <NuxtPage />
    <template v-if="route.path !== '/'">
      <SharedFooter />
    </template>
  </div>
</template>

<script setup>
import { useRoute } from 'vue-router';
const route = useRoute();
// No imports needed, Nuxt auto-imports components in Shared/
</script>
