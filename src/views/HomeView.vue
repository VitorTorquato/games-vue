<script setup lang="ts">

import GameCard from '@/components/GameCard/GameCard.vue';
import HeroSection from '@/components/Hero/HeroSection.vue';
import type { GameProps } from '@/utils/types/game.type';
import { onMounted, ref } from 'vue';

    const gameDaily = ref<GameProps | null>(null);
    const games = ref<GameProps[]>([]);

    const getGamesDaily = async () => {
        try{
          const response = await fetch(`https://sujeitoprogramador.com/next-api/?api=game_day`)
          const data = await response.json();
          gameDaily.value = data
        }catch(error){
          console.error("Something went wrong to fetch data" , error)
        }
      }

      const getGameDay = async () => {
        try{
          const response = await fetch(`https://sujeitoprogramador.com/next-api/?api=games`)
          const data =  await response.json();
          games.value = data
        }catch(error){
          console.error("Error to fetch data" , error)
        }
      }


    onMounted(async () => {
        getGamesDaily();
        getGameDay();
    })



 </script>

<template>
  <main class="w-full bg-black">
    <HeroSection :data="gameDaily"/>

    <div class="w-full bg-zinc-900 py-12">

      <h2 class="text-slate-200 text-3xl text-center mb-11">Jogos para conhecer</h2>

      <section class="container mx-auto grid gap-7 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 px-3">
          <GameCard v-for="game in games" :key="game.id" :data="game"/>
      </section>
    </div>
  </main>
</template>

