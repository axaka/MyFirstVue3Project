<script setup lang="ts">
import { defineProps, defineEmits } from "vue";

export type KingdomCardType = {
    portrait: string,
    name: string,
    job: string,
    motto: string,
}

const { portrait, name, job, motto } = defineProps<KingdomCardType>();

const emit = defineEmits<{
    (event: "emitAll", payload: KingdomCardType): void;
}>();

function select() {
    emit("emitAll", { portrait, name, job, motto });
}

</script>

<template>
    <button class="flip-card" @click="select">
        <div class="flip-card-inner">
            <div class="flip-card-front">
                <img :src="portrait" alt="Avatar">
            </div>
            <div class="flip-card-back">
                <h2>{{ job }}</h2>
                <h1>{{ name }}</h1>
                <p>{{ motto }}</p>
            </div>
        </div>
    </button>
</template>