<script setup>
import { useRoute, useRouter } from "vue-router";
import AppFooter from "~/components/layouts/default/AppFooter.vue";
import AppHeader from "~/components/layouts/default/AppHeader.vue";

const route = useRoute();
</script>
<template>
  <div class="flex min-h-screen flex-col bg-background">
    <AppHeader />
    <div class="flex-1">
      <div class="container flex-1 relative py-6 grid xl:grid-cols-12 gap-6">
        <div class="xl:col-span-2">
          <div class="sticky top-20">
            <div class="bg-muted p-1 rounded-md">
              <nav class="flex flex-col">
                <nuxt-link
                  to="/report/by-students"
                  class="text-sm p-2 rounded transition-all duration-300 cursor-pointer hover:bg-card"
                >
                  Talabalar(hisobot)
                </nuxt-link>
                <nuxt-link
                  to="/report/by-staff"
                  class="text-sm p-2 rounded transition-all duration-300 cursor-pointer hover:bg-card"
                >
                  Xodimlar(hisobot)
                </nuxt-link>
                <nuxt-link
                  to="/report/active-users"
                  class="text-sm p-2 rounded transition-all duration-300 cursor-pointer hover:bg-card"
                >
                  Faol talabalar
                </nuxt-link>
                <nuxt-link
                  to="/report/active-staff"
                  class="text-sm p-2 rounded transition-all duration-300 cursor-pointer hover:bg-card"
                >
                  Faol xodimlar
                </nuxt-link>
                <nuxt-link
                  to="/"
                  class="text-sm p-2 rounded transition-all duration-300 cursor-pointer hover:bg-card"
                >
                  Sovrindorlar
                </nuxt-link>
                <nuxt-link
                  to="/"
                  class="text-sm p-2 rounded transition-all duration-300 cursor-pointer hover:bg-card"
                >
                  Boshqa hisobotlar
                </nuxt-link>
              </nav>
            </div>
          </div>
        </div>
        <main class="xl:col-span-10">
          <slot />
        </main>
      </div>
    </div>
    <AppFooter />
  </div>
</template>
