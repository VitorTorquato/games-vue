<script setup lang="ts">
  import { defineProps } from 'vue';
  import type { GameProps } from '@/utils/types/game.type';
import { RouterLink } from 'vue-router';

  defineProps<{
    data:GameProps
  }>()

</script>

<template>
    <section class="w-full bg-slate-200 rounded-lg p-4 mb-5 overflow-hidden">
      <div class="w-full h-56 hover:scale-105 transition-all duration-300">
        <img class="object-cover w-full h-full rounded-lg" :src="data.image_url" :alt="data.title">
      </div>
      <div class="flex items-center justify-between mt-4">
        <div class="text-sm font-bold px-2 text-black text-ellipsis truncate whitespace-nowrap overflow-hidden">
          <RouterLink
            class="flex items-center gap-2"
            :to="`/games/${data.id}`"
          >{{ data.title }}<i class="pi pi-arrow-circle-right mr-2"></i></RouterLink>

        </div>
      </div>
    </section>
</template>
