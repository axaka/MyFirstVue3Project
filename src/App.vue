<script setup lang="ts">
import { ModalsContainer, useModal } from 'vue-final-modal'
import { RouterLink, RouterView } from "vue-router";

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
  <ModalsContainer />
  <RouterView />
</template>