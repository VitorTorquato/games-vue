<script setup lang="ts">
    import { RouterLink } from 'vue-router';
</script>

<template>
     <section>
      <div class="container m-auto py-6 px-6">
        <RouterLink
          to="/"
          class="text-white flex items-center"
        >
          <i class="pi pi-arrow-circle-left mr-2"></i>Games
        </RouterLink>
      </div>
    </section>
</template>
