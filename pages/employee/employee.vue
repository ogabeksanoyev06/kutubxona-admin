<script setup>
import {
  Table,
  TableBody,
  TableCaption,
  TableCell,
  TableHead,
  TableHeader,
  TableRow,
} from "@/components/ui/table";
</script>

<template>
  <section class="py-8 sm:py-10">
    <div class="container">
      <div class="grid grid-cols-1 gap-6 sm:grid-cols-12 mb-6">
        <div class="sm:col-span-6 md:col-span-4 lg:col-span-3">
          <Button>
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
              class="lucide lucide-download w-5 h-5 mr-2"
            >
              <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4" />
              <polyline points="7 10 12 15 17 10" />
              <line x1="12" x2="12" y1="15" y2="3" />
            </svg>
            Export talaba
          </Button>
        </div>
        <div class="sm:col-span-6 md:col-span-4 lg:col-span-3">
          <Select>
            <SelectTrigger>
              <SelectValue placeholder="Bo'limni tanlang" />
            </SelectTrigger>
            <SelectContent>
              <SelectGroup>
                <SelectItem value="apple"> Raqamli iqtisodiyot </SelectItem>
              </SelectGroup>
            </SelectContent>
          </Select>
        </div>
        <div class="sm:col-span-6 md:col-span-4 lg:col-span-3">
          <Select>
            <SelectTrigger>
              <SelectValue placeholder="Mehnat shaklini tanlang" />
            </SelectTrigger>
            <SelectContent>
              <SelectGroup>
                <SelectItem value="apple"> Raqamli iqtisodiyot </SelectItem>
              </SelectGroup>
            </SelectContent>
          </Select>
        </div>
        <div class="sm:col-span-6 md:col-span-4 lg:col-span-3">
          <Select>
            <SelectTrigger>
              <SelectValue placeholder="Statusni tanlang" />
            </SelectTrigger>
            <SelectContent>
              <SelectGroup>
                <SelectLabel>Fakultetlar</SelectLabel>
                <SelectItem value="apple"> Raqamli iqtisodiyot </SelectItem>
              </SelectGroup>
            </SelectContent>
          </Select>
        </div>

        <div class="sm:col-span-6 md:col-span-4 lg:col-span-6">
          <div class="relative w-full">
            <Input
              type="text"
              placeholder="Ism / Pasport / Xodim ID bo‘yicha qidirish"
              class="sm:pl-8"
            />
            <span
              class="absolute start-0 inset-y-0 flex items-center justify-center px-2"
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
                class="lucide lucide-scan-search w-5 h-5 text-muted-foreground hidden sm:flex"
              >
                <path d="M3 7V5a2 2 0 0 1 2-2h2" />
                <path d="M17 3h2a2 2 0 0 1 2 2v2" />
                <path d="M21 17v2a2 2 0 0 1-2 2h-2" />
                <path d="M7 21H5a2 2 0 0 1-2-2v-2" />
                <circle cx="12" cy="12" r="3" />
                <path d="m16 16-1.9-1.9" />
              </svg>
            </span>
          </div>
        </div>
      </div>
      <!-- <div class="space-y-1">
        <h1 class="text-2xl sm:text-3xl font-bold tracking-tight">Talabalar</h1>
        <p class="text-base sm:text-lg text-muted-foreground">
          Lorem ipsum dolor sit amet.
        </p>
      </div> -->
      <div class="border mb-2">
        <Table>
          <!-- <TableCaption>Talaba Hemis tizimida mavjud emas.</TableCaption> -->
          <TableHeader>
            <TableRow class="whitespace-nowrap">
              <TableHead> # </TableHead>
              <TableHead>Status</TableHead>
              <TableHead>Xodim</TableHead>
              <TableHead> Bo'linma </TableHead>
              <TableHead> Lavozim </TableHead>
              <TableHead> Stavka</TableHead>
              <TableHead>Buyruq raqami</TableHead>
            </TableRow>
          </TableHeader>
          <TableBody>
            <TableRow>
              <TableCell> 1 </TableCell>
              <TableCell>
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
                  class="lucide lucide-check w-5 h-5"
                >
                  <path d="M20 6 9 17l-5-5" />
                </svg>
              </TableCell>
              <TableCell>
                SEPATULLAYEV LUTFILLO BAXTIYORJON O‘G‘LI
                <p class="text-muted-foreground">336201100669</p>
              </TableCell>
              <TableCell>
                "Binary Graduate School" qo'shma fakulteti
              </TableCell>
              <TableCell>
                Tyutor
                <p class="text-muted-foreground">Ishlamoqda</p>
              </TableCell>
              <TableCell>
                0,50 stavka
                <p class="text-muted-foreground">
                  O‘rindoshlik (ichki-qo'shimcha)
                </p>
              </TableCell>
              <TableCell> <Switch id="airplane-mode" /></TableCell>
            </TableRow>
          </TableBody>
        </Table>
      </div>

      <Pagination
        v-slot="{ page }"
        :total="100"
        :sibling-count="1"
        show-edges
        :default-page="2"
        class="flex justify-end"
      >
        <PaginationList v-slot="{ items }" class="flex items-center gap-1">
          <PaginationPrev />

          <template v-for="(item, index) in items">
            <PaginationListItem
              v-if="item.type === 'page'"
              :key="index"
              :value="item.value"
              as-child
            >
              <Button
                class="w-9 h-9 p-0"
                :variant="item.value === page ? 'default' : 'outline'"
              >
                {{ item.value }}
              </Button>
            </PaginationListItem>
            <PaginationEllipsis v-else :key="item.type" :index="index" />
          </template>

          <PaginationNext />
        </PaginationList>
      </Pagination>
    </div>
  </section>
</template>
