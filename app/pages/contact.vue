<script
  setup
  lang="ts"
></script>

<template>
  <UContainer>
    <div class="pt-32 w-full max-w-2xl mx-auto min-h-screen">
      <h1 class="text-3xl font-semibold mb-8 text-left">Contact</h1>
      <p class="text-muted-foreground text-left ">You can reach me via email at <a
          href="mailto:hello@michaelsynan.com"
          class="underline-thick hover:text-foreground "
        >hello [at] michaelsynan [dot] com</a> or on GitHub at <a
          href="https://github.com/michaelsynan"
          target="_blank"
          class="underline-thick hover:text-foreground"
        >michaelsynan</a>.</p>
      <div class="flex flex-row gap-4 w-full justify-start pt-4">
        <UIcon
          name="i-mdi-github"
          class="w-6 h-6 text-muted-foreground hover:text-foreground transition-colors cursor-pointer"
        />
        <UIcon
          name="i-mdi-linkedin"
          class="w-6 h-6 text-muted-foreground hover:text-foreground transition-colors cursor-pointer"
        />
        <UIcon
          name="i-mdi-mastodon"
          class="w-6 h-6 text-muted-foreground hover:text-foreground transition-colors cursor-pointer"
        />
      </div>

    </div>
  </UContainer>
</template>

<style scoped></style>
