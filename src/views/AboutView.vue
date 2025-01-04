<script setup lang="ts">
import kingdomCard, { type KingdomCardType } from "../components/cards/kingdomCard.vue";
import audienceRequestForm from "@/components/cards/audienceRequestForm.vue";

import { ref } from "vue";
import { useModal } from "vue-final-modal";

// Define a reactive object to hold the modal's attributes
const modalAttrs = ref<KingdomCardType & { onConfirm: () => void }>({
  portrait: 'portrait',
  name: 'name',
  job: 'job',
  motto: 'motto',
  onConfirm: () => { close() }
});

// Modal setup
const { open, close } = useModal({
  component: audienceRequestForm,
  attrs: modalAttrs.value,
});

function openContact(card: KingdomCardType) {

  modalAttrs.value.job = card.job;
  modalAttrs.value.motto = card.motto;
  modalAttrs.value.name = card.name;
  modalAttrs.value.portrait = card.portrait;
  modalAttrs.value.onConfirm = () => {
    close();
  }

  // modalAttrs.value = {
  //   ...card,
  //   onConfirm() {
  //     close(); // Close the modal after confirming
  //   },
  // };

  open(); // Open the modal
}



</script>

<template>
  <main>
    <section id="about" class="container flexi">
      <h1>About</h1>
      <p class="full">Welcome to the kingdom of Medivelia</p>
    </section>

    <section id="cards" class="container flexi">
      <!-- Pass props to each kingdomCard and listen for emit-all -->
      <kingdomCard portrait="/img/King.webp" name="Rand" job="King"
        motto="Strength secures the crown; wisdom preserves it." @emit-all="openContact" />
      <kingdomCard portrait="/img/Queen.webp" name="Renee" job="Queen"
        motto="Grace commands loyalty; charm conquers all." @emit-all="openContact" />
      <kingdomCard portrait="/img/Finance.webp" name="Verrick" job="Minister of Coin"
        motto="A coin saved is a kingdom earned." @emit-all="openContact" />
      <kingdomCard portrait="/img/Knight.webp" name="Croakie" job="Knight"
        motto="If someone gets past me uninvited, something is wrong with the world." @emit-all="openContact" />
      <kingdomCard portrait="/img/Scholarch.webp" name="Viseidous" job="Advisor" motto="I wonder. How DID that happen?"
        @emit-all="openContact" />
    </section>
  </main>
</template>
