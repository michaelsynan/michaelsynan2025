<script setup lang="ts">
const projects = [
  {
    title: 'Formwork Studios',
    description: 'Design-driven web studio for meaningful online experiences.',
    tags: ['Web Design', 'SEO'],
    link: 'https://formworkstudios.com',
    image: '/formwork.webp',
  },
  {
    title: 'Primo Sewer Cleaning',
    description: 'Minimalist e-commerce for a modern brand.',
    tags: ['E-Commerce', 'Branding'],
    link: 'https://primo-sewer-cleaning.com',
    image: '/primo.webp',
  },
  {
    title: 'Red Light Bed Consulting',
    description: 'Landing page for a wellness product.',
    tags: ['Consulting', 'Landing Page'],
    link: 'https://redlightbed.com',
    image: '/redlight.webp',
  },
  {
    title: 'Shan Shan Peer Coaching',
    description: 'Coaching and mentorship platform.',
    tags: ['Coaching', 'Mentorship'],
    link: 'https://www.shanshansongpeercoaching.com/',
    image: '/shan.webp',
  },
];
</script>

<template>
  <UContainer>
    <div class="pt-32 px-4 w-full max-w-3xl mx-auto min-h-screen">
      <h1 class="text-3xl font-bold mb-2">Projects</h1>
      <p class="pb-6">Some of my recent work.</p>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <NuxtLink v-for="project in projects" :key="project.title" :to="project.link" target="_blank"
          class="relative group w-full block focus:outline-none">
          <div class="relative w-full flex items-center justify-center bg-neutral-100 border border-neutral-200"
            style="min-height: 120px; min-width: 100%;">
            <NuxtImg :src="project.image" alt="Project image"
              class="block max-w-full max-h-full h-auto rounded-none w-full" style="display: block; margin: 0 auto;" />
            <div
              class="absolute left-0 bottom-0 w-full flex flex-wrap gap-2 justify-end items-end p-3 pointer-events-none group-hover:opacity-100 group-hover:translate-y-0 opacity-0 translate-y-4 transition-all duration-300">
              <span v-for="tag in project.tags" :key="tag"
                class="text-[10px] font-mono text-white bg-neutral-900/90 px-2 py-1 border border-neutral-800 rounded-none">
                {{ tag }}
              </span>
            </div>
          </div>
          <div class="flex flex-col items-start mt-2 ml-1">
            <h3 class="text-xs font-normal m-0 p-0 text-neutral-900" style="font-size:0.8rem;line-height:1.1;">
              {{ project.title }}
            </h3>
            <p class="text-xs text-neutral-500 mb-1">{{ project.description }}</p>
            <span class="text-[11px] text-neutral-700 font-mono flex items-center gap-1">
              View Project
              <UIcon name="i-mdi-arrow-top-right-thick" class="w-4 h-4" />
            </span>
          </div>
        </NuxtLink>
      </div>
    </div>
  </UContainer>
</template>

<style scoped>
/* Ultra minimalist, image-focused card styles handled by Tailwind */
</style>
