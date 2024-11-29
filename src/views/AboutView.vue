<script setup lang="ts">
import { ref } from "vue";
import aboutCard from "../components/cards/aboutCard.vue"
import audienceRequestForm from "@/components/cards/audienceRequestForm.vue";

import { ModalsContainer, useModal } from 'vue-final-modal'

const { open, close } = useModal({
  component: audienceRequestForm,
  attrs: {
    name: 'Hello World!',
    onConfirm() {
      close()
    },
  },
  slots: {
    default: '<p>The content of the modal</p>',
  },
})

const toRef = ref("");
const formRef = ref<HTMLElement | null>(null);

function scrollToForm() {
  if (formRef.value instanceof HTMLElement) {
    formRef.value.scrollIntoView({ behavior: "smooth" });
  } else {
    console.log("formRef is not a valid HTMLElement");
  }
}

</script>

<template>
  <main>
    <section id="about" class="container flexi">
      <h1>About</h1>
      <p class="full">Welcome to the kingdom of Medivelia</p>
      <VButton @click="open">
        Open Modal
      </VButton>
    </section>

    <section id="cards" class="container flexi">
      <aboutCard v-model="toRef" @update:to="scrollToForm" portrait="/img/King.webp" name="" job="King" motto="..." />
      <aboutCard v-model="toRef" @update:to="scrollToForm" portrait="/img/Queen.webp" name="" job="Queen" motto="..." />

      <aboutCard v-model="toRef" @update:to="scrollToForm" portrait="/img/Knight.webp" name="Croakie" job="Knight"
        motto="If someone get's past me uninvited, something is wrong with the world." />

      <aboutCard v-model="toRef" @update:to="scrollToForm" portrait="/img/Scholarch.webp" name="Viseidous" job="Advisor"
        motto="I wonder. How DID that happen?" />
      <aboutCard v-model="toRef" @update:to="scrollToForm" portrait="/img/Scholarch.webp" name="Viseidous"
        job="Scholarch" motto="I wonder. How DID that happen?" />
    </section>

    <!-- <section id="request">
      <div class="full flexi mt-12">
        <audienceRequestForm v-model="toRef" ref="formRef" />
      </div>

    </section> -->


  </main>
</template>
