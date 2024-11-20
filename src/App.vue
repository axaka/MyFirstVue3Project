<script setup lang="ts">
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</routerLink>
        <RouterLink to="/about">About</routerLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<script>
  import { RouterLink, RouterView } from "vue-router";
</script>