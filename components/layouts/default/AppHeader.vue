<script setup>
import { useMagicKeys } from "@vueuse/core";

import { ref, watch } from "vue";

import { useRoute, useRouter } from "vue-router";

const route = useRoute();

import {
  CommandDialog,
  CommandEmpty,
  CommandGroup,
  CommandInput,
  CommandItem,
  CommandList,
  CommandSeparator,
} from "@/components/ui/command";

const menu = [
  {
    title: "Asosiy",
    route: "/",
  },
  {
    title: "Talabalar ro`yxati",
    route: "/student/student",
  },
  {
    title: "Xodimlar ro`yxati",
    route: "/employee/employee",
  },
  {
    title: "Hisobotlar",
    route: "/report",
  },
  {
    title: "Statistika",
    route: "/statistical",
  },
];

const colorMode = useColorMode();

const isDark = computed({
  get() {
    return colorMode.value === "dark";
  },
  set() {
    colorMode.preference = colorMode.value === "dark" ? "light" : "dark";
  },
});

const open = ref(false);

function handleOpenChange() {
  open.value = !open.value;
}
</script>

<template>
  <header
    class="sticky z-40 top-0 bg-background/30 backdrop-blur-lg border-b border-border"
  >
    <div class="container flex h-14 items-center">
      <div class="mr-4 md:mr-1 flex">
        <NuxtLink
          to="/"
          class="mr-4 md:mr-2 lg:mr-6 flex items-center lg:space-x1 xl:space-x-2"
        >
          <svg
            width="76"
            height="65"
            viewBox="0 0 76 65"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
            class="w-5 h-5"
          >
            <path d="M37.5274 0L75.0548 65H0L37.5274 0Z" fill="#000000" />
          </svg>
          <span class="text-lg font-bold whitespace-nowrap"> Kutubxona </span>
        </NuxtLink>
        <nav
          class="hidden md:flex items-center max-lg:space-x-4 space-x-6 text-sm font-medium"
        >
          <NuxtLink
            v-for="(item, i) in menu"
            :key="i"
            :to="item.route"
            class="transition-colors hover:text-foreground/80 text-foreground/60"
            :class="{ '!text-foreground': item.route === route.path }"
          >
            {{ item.title }}
          </NuxtLink>
        </nav>
      </div>
      <div class="flex flex-1 items-center space-x-2 justify-end">
        <nav class="flex items-center">
          <Button
            size="icon"
            variant="ghost"
            @click="handleOpenChange"
            class="max-sm:h-8 max-sm:w-8"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
              class="lucide lucide-search w-5 h-5"
            >
              <circle cx="11" cy="11" r="8"></circle>
              <path d="m21 21-4.3-4.3"></path>
            </svg>
          </Button>
          <CommandDialog v-model:open="open">
            <CommandInput placeholder="Type a command or search..." />
            <CommandList>
              <CommandEmpty>No results found.</CommandEmpty>
              <CommandGroup heading="Suggestions">
                <CommandItem value="calendar"> Calendar </CommandItem>
                <CommandItem value="search-emoji"> Search Emoji </CommandItem>
                <CommandItem value="calculator"> Calculator </CommandItem>
              </CommandGroup>
              <CommandSeparator />
              <CommandGroup heading="Settings">
                <CommandItem value="profile"> Profile </CommandItem>
                <CommandItem value="billing"> Billing </CommandItem>
                <CommandItem value="settings"> Settings </CommandItem>
              </CommandGroup>
            </CommandList>
          </CommandDialog>
          <div class="relative flex" @click="isDark = !isDark">
            <Button
              variant="ghost"
              size="icon"
              class="absolute max-sm:h-8 max-sm:w-8"
            >
              <svg
                viewBox="0 0 15 15"
                width="1.2em"
                height="1.2em"
                class="w-5 h-5 text-foreground rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100"
              >
                <path
                  fill="currentColor"
                  fill-rule="evenodd"
                  d="M7.5 0a.5.5 0 0 1 .5.5v2a.5.5 0 0 1-1 0v-2a.5.5 0 0 1 .5-.5M2.197 2.197a.5.5 0 0 1 .707 0L4.318 3.61a.5.5 0 0 1-.707.707L2.197 2.904a.5.5 0 0 1 0-.707M.5 7a.5.5 0 0 0 0 1h2a.5.5 0 0 0 0-1zm1.697 5.803a.5.5 0 0 1 0-.707l1.414-1.414a.5.5 0 1 1 .707.707l-1.414 1.414a.5.5 0 0 1-.707 0M12.5 7a.5.5 0 0 0 0 1h2a.5.5 0 0 0 0-1zm-1.818-2.682a.5.5 0 0 1 0-.707l1.414-1.414a.5.5 0 1 1 .707.707L11.39 4.318a.5.5 0 0 1-.707 0M8 12.5a.5.5 0 0 0-1 0v2a.5.5 0 0 0 1 0zm2.682-1.818a.5.5 0 0 1 .707 0l1.414 1.414a.5.5 0 1 1-.707.707l-1.414-1.414a.5.5 0 0 1 0-.707M5.5 7.5a2 2 0 1 1 4 0a2 2 0 0 1-4 0m2-3a3 3 0 1 0 0 6a3 3 0 0 0 0-6"
                  clip-rule="evenodd"
                ></path>
              </svg>
            </Button>
            <Button variant="ghost" size="icon" class="max-sm:h-8 max-sm:w-8">
              <svg
                viewBox="0 0 15 15"
                width="1.2em"
                height="1.2em"
                class="w-5 h-5 text-foreground rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0"
              >
                <path
                  fill="currentColor"
                  fill-rule="evenodd"
                  d="M2.9.5a.4.4 0 0 0-.8 0v.6h-.6a.4.4 0 1 0 0 .8h.6v.6a.4.4 0 1 0 .8 0v-.6h.6a.4.4 0 0 0 0-.8h-.6zm3 3a.4.4 0 1 0-.8 0v.6h-.6a.4.4 0 1 0 0 .8h.6v.6a.4.4 0 1 0 .8 0v-.6h.6a.4.4 0 0 0 0-.8h-.6zm-4 3a.4.4 0 1 0-.8 0v.6H.5a.4.4 0 1 0 0 .8h.6v.6a.4.4 0 0 0 .8 0v-.6h.6a.4.4 0 0 0 0-.8h-.6zM8.544.982l-.298-.04c-.213-.024-.34.224-.217.4A6.57 6.57 0 0 1 9.203 5.1a6.602 6.602 0 0 1-6.243 6.59c-.214.012-.333.264-.183.417a6.8 6.8 0 0 0 .21.206l.072.066l.26.226l.188.148l.121.09l.187.131l.176.115c.12.076.244.149.37.217l.264.135l.26.12l.303.122l.244.086a6.568 6.568 0 0 0 1.103.26l.317.04l.267.02a6.6 6.6 0 0 0 6.943-7.328l-.037-.277a6.557 6.557 0 0 0-.384-1.415l-.113-.268l-.077-.166l-.074-.148a6.602 6.602 0 0 0-.546-.883l-.153-.2l-.199-.24l-.163-.18l-.12-.124l-.16-.158l-.223-.2l-.32-.26l-.245-.177l-.292-.19l-.321-.186l-.328-.165l-.113-.052l-.24-.101l-.276-.104l-.252-.082l-.325-.09l-.265-.06zm1.86 4.318a7.578 7.578 0 0 0-.572-2.894a5.601 5.601 0 1 1-4.748 10.146a7.61 7.61 0 0 0 3.66-2.51a.749.749 0 0 0 1.355-.442a.75.75 0 0 0-.584-.732c.062-.116.122-.235.178-.355A1.25 1.25 0 1 0 10.35 6.2c.034-.295.052-.595.052-.9"
                  clip-rule="evenodd"
                ></path>
              </svg>
            </Button>
          </div>

          <Button size="icon" variant="ghost" class="max-sm:h-8 max-sm:w-8">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
              class="lucide lucide-log-in h-5 w-5"
            >
              <path d="M15 3h4a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2h-4"></path>
              <polyline points="10 17 15 12 10 7"></polyline>
              <line x1="15" x2="3" y1="12" y2="12"></line>
            </svg>
          </Button>
          <Button
            class="inline-flex md:hidden max-sm:h-8 max-sm:w-8"
            size="icon"
            variant="ghost"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
              class="lucide lucide-menu w-5 h-5"
            >
              <line x1="4" x2="20" y1="12" y2="12" />
              <line x1="4" x2="20" y1="6" y2="6" />
              <line x1="4" x2="20" y1="18" y2="18" />
            </svg>
          </Button>
        </nav>
      </div>
    </div>
  </header>
</template>
