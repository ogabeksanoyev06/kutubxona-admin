<script setup>
import AppFooter from "~/components/layouts/default/AppFooter.vue";
import AppHeader from "~/components/layouts/default/AppHeader.vue";
</script>
<template>
  <div class="relative flex min-h-screen flex-col bg-background">
    <AppHeader />
    <main class="flex-1 pt-6 pb-12">
      <div class=""><slot /></div>
    </main>
    <AppFooter />
  </div>
</template>
