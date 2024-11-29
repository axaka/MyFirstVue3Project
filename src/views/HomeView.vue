<script setup lang="ts">
import { ref } from "vue";
const count = ref(0);
</script>

<template>
  <main>
    <h1 class="text-3xl font-bold underline">Home</h1>
    <span class="loading loading-spinner text-primary"></span>
    <p>
      This is my first ever Vue project! It's pretty cool, looking forward to
      play around with it.
    </p>

    <section>
      <h1 class="mt-3 text-3xl">Counter</h1>
      <button class="btn btn-warning" @click="count--">-</button>
      <span>Counter is {{ count }} .</span>
      <button class="btn btn-success" @click="count++">+</button>
    </section>
  </main>
</template>
