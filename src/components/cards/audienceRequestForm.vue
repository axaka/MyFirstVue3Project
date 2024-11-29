<script setup lang="ts">
import { ref, defineProps } from "vue";

import { VueFinalModal } from 'vue-final-modal';

// const count = ref(0);
defineProps({
    portrait: String,
    name: String,
    job: String,
    motto: String,
    to: String,
})

const emit = defineEmits<{
    (e: 'confirm'): void
}>()

</script>

<template>
    <VueFinalModal class="confirm-modal" content-class="confirm-modal-content" overlay-transition="vfm-fade"
        content-transition="vfm-fade">



        <div ref="formRef" class="w-full max-w-lg">
            <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4" id="form">

                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2" for="to">
                        To
                    </label>
                    <input readonly :value="to"
                        class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                        id="to" type="text" placeholder="To">
                </div>

                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2" for="from">
                        From
                    </label>
                    <input
                        class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                        id="from" type="text" placeholder="From">
                </div>

                <div class="mb-6">
                    <label class="block text-gray-700 text-sm font-bold mb-2" for="title">
                        Title
                    </label>
                    <input
                        class="shadow appearance-none border border-red-500 rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
                        id="title" type="text" placeholder="Title">
                    <p class="text-red-500 text-xs italic">We do not tolerate that anyone make a request to speak!</p>
                </div>

                <div class="mb-6">
                    <label class="block text-gray-700 text-sm font-bold mb-2" for="request">
                        Request
                    </label>
                    <textarea
                        class="shadow appearance-none border border-red-500 rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"
                        style="min-height: 150px;" name="request" id="request" placeholder="Request"></textarea>

                    <!-- <p class="text-red-500 text-xs italic">We do not tolerate that anyone make a request to speak!</p> -->
                </div>

                <div class="flex items-center justify-between">
                    <button @click="emit('confirm')"
                        class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
                        type="button">
                        Make request
                    </button>

                    <a class="inline-block align-baseline font-bold text-sm text-blue-500 hover:text-blue-800" href="#">
                        Forget it, maybe another time
                    </a>
                </div>
            </form>
        </div>
    </VueFinalModal>
</template>