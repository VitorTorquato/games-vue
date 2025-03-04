<script setup lang="ts">
    import { defineProps } from 'vue';

    defineProps({
      link:{
        type:String
      },
      src:{
        type:String,
      },
      alt:{
        type:String
      }
    })


</script>

<template>
    <div class="container mx-auto bg-black py-9">
      <section class="w-full max-w-6xl md:h-[500px] mx-auto flex flex-col md:flex-row items-center justify-center gap-24 px-2 py-3">
        <div class="space-y-4 flex flex-col items-center text-white gap-4 md:gap-9">
            <p class="text-3xl md:text-5xl text-center">Cada dia um jogo diferente para voce se divertir!</p>
            <a  class="border-2 border-slate-500 rounded-md p-2 font-normal text-base md:text-2xl hover:scale-105 duration-300" href="#">{{ link }}</a>
        </div>
        <div class="rounded-md overflow-hidden">
            <img class="object-cover object-center" :src=src :alt=alt>
        </div>
      </section>
    </div>

</template>
