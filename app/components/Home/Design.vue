<template>
  <div class="flex flex-row items-start gap-4 overflow-hidden w-full h-[500px]">
    <div class="flex-1 h-full overflow-hidden flex items-start">
      <NuxtImg src="/work/80.png" alt="Work 80" placeholder class="object-cover object-top h-full w-full img-border"
        style="min-width: 0;" />
    </div>
    <div class="flex-1 h-full overflow-hidden flex items-start">
      <NuxtImg src="/work/physicalmind.png" placeholder alt="Physical Mind"
        class="object-cover object-top h-full w-full img-border" style="min-width: 0;" />
    </div>
    <div class="flex-1 h-full overflow-hidden flex items-start">
      <NuxtImg src="/work/redlightbed.png" placeholder alt="Red Light Bed"
        class="object-cover object-top h-full w-full img-border" style="min-width: 0;" />
    </div>
    <div class="flex-1 h-full overflow-hidden flex items-start">
      <NuxtImg src="/work/shanshansong.png" placeholder alt="Shanshan Song"
        class="object-cover object-top h-full w-full img-border" style="min-width: 0;" />
    </div>
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
.img-border {
  border-width: 1px;
  border-style: solid;
  border-color: #e5e7eb;
  /* Tailwind gray-200 */
}
</style>
