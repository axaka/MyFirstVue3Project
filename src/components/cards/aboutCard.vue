<script setup lang="ts">
import { defineProps, defineEmits } from "vue";

defineProps({
    portrait: String,
    name: String,
    job: String,
    motto: String,
    to: String,
});

const emit = defineEmits(["update:to"]);

function select(value: string | undefined) {
    emit("update:to", value);
}

</script>

<template>
    <button class="flip-card" @click="select(name)">
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