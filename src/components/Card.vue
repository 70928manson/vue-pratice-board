<script setup>
import { defineProps } from 'vue';

defineProps({
    bg: {
        type: String,
        default: 'bg-gray-100'
    },
    title: {
        type: String,
        default: 'title'
    },
    description: {
        type: String,
        default: 'description'
    },
    buttonBg: {
        type: String,
        default: 'bg-black'
    },
    buttonText: {
        type: String,
        default: 'button text'
    }
})
</script>

<template>
    <div :class="`${bg} p-6 rounded-lg shadow-md`">
        <h2 class="text-2xl font-bold">{{ title }}</h2>
        <p class="mt-2 mb-4">
            {{ description }}
        </p>
        <a href="jobs.html" :class="`inline-block ${buttonBg} text-white rounded-lg px-4 py-2 hover:bg-gray-700`">
            {{ buttonText }}
        </a>
    </div>
</template>