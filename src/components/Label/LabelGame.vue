<script setup lang="ts">
    import { defineProps } from 'vue';

    defineProps({
      name: String
    })
</script>

<template>
    <div class="flex-grow sm:flex-grow-0 py-1 px-3 bg-slate-200 text-black text-center rounded-xl fover:font-bold duration-500">
        {{ name }}
    </div>
</template>
