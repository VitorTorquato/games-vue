<script setup lang="ts">

import HeroSection from '@/components/Hero/HeroSection.vue';
import type { GameProps } from '@/utils/types/game.type';
import { onMounted, ref } from 'vue';

    const game = ref<GameProps | null>(null)

    const getGamesDaily = async () => {
        try{
          const response = await fetch(`https://sujeitoprogramador.com/next-api/?api=game_day`)
          const data = await response.json();
          game.value = data
        }catch(error){
          console.error("Something went wrong to fetch data" , error)
        }
      }


    onMounted(async () => {
        getGamesDaily();
    })



 </script>

<template>
  <main class="w-full">
    <HeroSection :link="game?.title" :src="game?.image_url" :alt="game?.title"/>
  </main>
</template>

