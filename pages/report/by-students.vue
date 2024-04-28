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

import {
  Pagination,
  PaginationEllipsis,
  PaginationFirst,
  PaginationLast,
  PaginationList,
  PaginationListItem,
  PaginationNext,
  PaginationPrev,
} from "@/components/ui/pagination";

import { Button } from "@/components/ui/button";

definePageMeta({
  layout: "report",
});
</script>

<template>
  <section>
    <div class="grid gap-6 sm:grid-cols-12 mb-6">
      <div class="sm:col-span-6 lg:col-span-3">
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
          Yuklab olish
        </Button>
      </div>
      <div class="sm:col-span-6 lg:col-span-3">
        <Select>
          <SelectTrigger>
            <SelectValue placeholder="Fakultetni tanlang" />
          </SelectTrigger>
          <SelectContent>
            <SelectGroup>
              <SelectLabel>Fakultetlar</SelectLabel>
              <SelectItem value="apple"> Raqamli iqtisodiyot </SelectItem>
            </SelectGroup>
          </SelectContent>
        </Select>
      </div>
      <div class="sm:col-span-6 lg:col-span-3">
        <Select>
          <SelectTrigger>
            <SelectValue placeholder="O'quv rejani tanlang" />
          </SelectTrigger>
          <SelectContent>
            <SelectGroup>
              <SelectItem value="apple"> Raqamli iqtisodiyot </SelectItem>
            </SelectGroup>
          </SelectContent>
        </Select>
      </div>
      <div class="sm:col-span-6 lg:col-span-3">
        <Select>
          <SelectTrigger>
            <SelectValue placeholder="Semestrni tanlang" />
          </SelectTrigger>
          <SelectContent>
            <SelectGroup>
              <SelectItem value="apple"> Raqamli iqtisodiyot </SelectItem>
            </SelectGroup>
          </SelectContent>
        </Select>
      </div>
      <div class="sm:col-span-6 lg:col-span-3">
        <Select>
          <SelectTrigger>
            <SelectValue placeholder="Guruhni tanlang" />
          </SelectTrigger>
          <SelectContent>
            <SelectGroup>
              <SelectLabel>Guruhlar</SelectLabel>
              <SelectItem value="apple"> Raqamli iqtisodiyot </SelectItem>
            </SelectGroup>
          </SelectContent>
        </Select>
      </div>
      <div class="sm:col-span-6 lg:col-span-3">
        <Select>
          <SelectTrigger>
            <SelectValue placeholder="Kursni tanlang" />
          </SelectTrigger>
          <SelectContent>
            <SelectGroup>
              <SelectItem value="apple"> Raqamli iqtisodiyot </SelectItem>
            </SelectGroup>
          </SelectContent>
        </Select>
      </div>
    </div>
    <div class="border mb-2">
      <Table>
        <TableHeader>
          <TableRow class="whitespace-nowrap">
            <TableHead> # </TableHead>
            <TableHead>Talaba</TableHead>
            <TableHead>Fakultet</TableHead>
            <TableHead> Mutaxassislik </TableHead>
            <TableHead>Ta’lim turi </TableHead>
            <TableHead>Guruh</TableHead>
            <TableHead>Tashriflar soni</TableHead>
          </TableRow>
        </TableHeader>
        <TableBody class="whitespace-nowrap">
          <TableRow v-for="(item, i) in 10" :key="item">
            <TableCell> {{ i + 1 }} </TableCell>
            <TableCell>
              SEPATULLAYEV LUTFILLO BAXTIYORJON O‘G‘LI
              <p class="text-muted-foreground">336201100669</p>
            </TableCell>
            <TableCell> Raqamli iqtisodiyot</TableCell>
            <TableCell>
              5230600
              <p class="text-muted-foreground">Davlat granti</p>
            </TableCell>
            <TableCell>
              Bakalavr
              <p class="text-muted-foreground">Kunduzgi</p>
            </TableCell>
            <TableCell> ММТ-80i</TableCell>
            <TableCell>200</TableCell>
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
  </section>
</template>
