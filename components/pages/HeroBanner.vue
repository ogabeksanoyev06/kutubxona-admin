<script setup>
import { Button } from "~/components/ui/button";
</script>

<template>
  <section class="py-8 md:py-12 md:pb-8 lg:py-24 lg:pb-10">
    <div class="flex flex-col items-center justify-center gap-y-6">
      <div
        class="inline-flex items-center border rounded-full bg-muted px-3 py-1.5 text-sm font-medium"
      >
        <span>✨</span>
        <div class="shrink-0 bg-border w-px mx-2 h-4"></div>
        <span>Xush kelibsiz xodim</span>
      </div>
      <div class="flex flex-col items-center gap-y-6">
        <div
          class="text-center max-w-4xl text-3xl md:text-4xl lg:text-6xl font-bold lg:leading-snug"
        >
          <span class="text-balance">
            Toshkent davlat iqtisodiyot universiteti
          </span>
        </div>
        <div
          class="text-center text-base sm:text-xl text-muted-foreground max-w-4xl"
        >
          <span> Talabalar va xodimlarni ro'yxatga olish tizimi </span>
        </div>
      </div>

      <div class="flex justify-center space-x-2 md:space-x-4">
        <nuxt-link to="/">
          <Button class="rounded-full" size="lg">Hisobotlar</Button>
        </nuxt-link>
      </div>
    </div>
  </section>
</template>
