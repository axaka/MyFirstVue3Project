<script setup lang="ts">
import { ModalsContainer } from 'vue-final-modal';
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <header class="w-full bg-blue-600 text-white shadow">
    <div class="max-w-7xl mx-auto px-4 py-4 flex justify-between items-center">
      <h1 class="text-xl font-bold">KingDOOM</h1>
      <nav class="space-x-4">
        <RouterLink to="/" class="text-white hover:text-blue-300 transition">Home</RouterLink>
        <RouterLink to="/about" class="text-white hover:text-blue-300 transition">About</RouterLink>
      </nav>
    </div>
  </header>
  <main class="min-h-screen bg-blue-300">
    <ModalsContainer />
    <RouterView />
  </main>
</template>
