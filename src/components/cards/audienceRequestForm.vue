<script setup lang="ts">
import { defineProps, defineEmits } from "vue";

import type { KingdomCardType } from "./kingdomCard.vue";
import { VueFinalModal } from 'vue-final-modal';

const { portrait, name, job, motto } = defineProps<KingdomCardType>();

const emit = defineEmits<{
    (e: 'confirm'): void
}>();
</script>

<template>
    <VueFinalModal class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-50"
        content-class="confirm-modal-content max-h-screen overflow-auto" overlay-transition="vfm-fade"
        content-transition="vfm-fade">
        <div ref="formRef" class="w-full max-w-lg">
            <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4" id="form">

                <div class="mb-4">
                    <img :src="portrait" alt="" class="w-full h-auto mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2" for="to">
                        To
                    </label>
                    <input disabled
                        class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-100 leading-tight"
                        id="to" type="text" placeholder="To" :value="`${job} - ${name}`" />
                </div>

                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2" for="title">
                        Title
                    </label>
                    <input
                        class="shadow appearance-none border border-red-500 rounded w-full py-2 px-3 text-gray-100 mb-3 leading-tight focus:outline-none focus:shadow-outline"
                        id="title" type="text" placeholder="Title" />
                </div>

                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2" for="request">
                        Request
                    </label>
                    <textarea
                        class="shadow appearance-none border border-red-500 rounded w-full py-2 px-3 text-gray-100 mb-3 leading-tight focus:outline-none focus:shadow-outline"
                        style="min-height: 150px;" name="request" id="request" placeholder="Request"></textarea>
                </div>

                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2" for="from">
                        From
                    </label>
                    <input
                        class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-100 leading-tight focus:outline-none focus:shadow-outline"
                        id="from" type="text" placeholder="From" />
                    <p class="text-red-500 text-xs italic">
                        We do not tolerate just anyone make a request to speak!
                    </p>
                </div>

                <div class="flex items-center justify-between">
                    <button type="submit"
                        class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">
                        Make request
                    </button>

                    <button @click="emit('confirm')"
                        class="inline-block align-baseline font-bold text-sm text-blue-500 hover:text-blue-800"
                        type="button">
                        Forget it, maybe another time
                    </button>
                </div>
            </form>
        </div>
    </VueFinalModal>
</template>
