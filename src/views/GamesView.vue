<script setup lang="ts">
    import BackButton from '@/components/BackButton/BackButton.vue';
import LabelGame from '@/components/Label/LabelGame.vue';
import type { GameProps } from '@/utils/types/game.type';
import { onMounted, reactive } from 'vue';
import { useRoute } from 'vue-router';

    const route = useRoute();
    const gameId = route.params.id;

    const state = reactive({
      game: {} as GameProps,
    })

    onMounted(async () => {
      try{
        const response = await fetch(`https://sujeitoprogramador.com/next-api/?api=game&id=${gameId}`)
        const data = await response.json();
        state.game = data
      }catch(error){
        console.error("Something went wrong" , error)
      }
    })

</script>

<template>
    <main class="w-full">
      <div class="w-full bg-black">
        <section class="container md:h-[500px] mx-auto flex flex-col md:flex-row items-center justify-center gap-24 px-2 py-3">
          <div class="space-y-4 flex flex-col items-center text-white gap-4 md:gap-9">
              <p class="text-3xl md:text-5xl text-center">{{ state.game.title }}</p>
              <BackButton/>
          </div>
          <div class="rounded-md overflow-hidden">
            <img class="object-cover object-center"  :src="state.game.image_url" :alt="state.game.title">
          </div>
        </section>
      </div>

      <section class="max-w-6xl mx-auto bg-white text-black flex justify-between mt-9">
          <div class="w-full max-w-[700px]">
            <h2 class="text-2xl font-bold my-4">Descricao</h2>
              <p class="text-base">{{ state.game.description }}</p>
          </div>

          <div class="flex flex-col">
            <h2 class="text-2xl font-bold my-4">Plataformas</h2>
            <div class="flex gap-3">
              <LabelGame v-for="item in state.game.platforms" :key="item" :name="item"/>
            </div>
            <h2 class="text-2xl font-bold my-4">Categorias</h2>
            <div class="flex gap-3">
              <LabelGame v-for="item in state.game.categories" :key="item" :name="item"/>
            </div>
            <p className="mt-7 mb-2">
                      <strong>Data de lançamento:</strong> {{ state.game.release }}
             </p>
          </div>



      </section>
    </main>
</template>
