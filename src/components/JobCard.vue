<script setup>
import { defineProps, computed, ref } from "vue";

const props = defineProps({
  job: Object,
});

const showFullDescription = ref(false);
</script>

<template>
  <div class="bg-white rounded-xl shadow-md relative flex flex-col">
    <div class="p-4 flex flex-col flex-grow">
      <div class="mb-6">
        <div class="text-gray-600 my-2">{{ job.type }}</div>
        <h3 class="text-xl font-bold">{{ job.title }}</h3>
      </div>

      <div class="mb-5 flex-grow">
        {{ job.description }}
      </div>

      <!--這裡跟 description 區隔 -->
      <h3 class="text-green-500 mb-2">{{ job.salary }} / Year</h3>

      <div class="border border-gray-100 mb-5"></div>

      <div class="flex flex-col lg:flex-row justify-between mb-4">
        <div class="text-orange-700 mb-3">
          <i class="fa-solid fa-location-dot text-lg"></i>
          {{ job.location }}
        </div>
        <a
          :href="`/job/${job.id}`"
          class="h-[36px] bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-lg text-center text-sm"
        >
          Read More
        </a>
      </div>
    </div>
  </div>
</template>