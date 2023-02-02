<script setup lang="ts">
import { ref } from "vue";
import DayColumn from "./DayColumn.vue";
const days = ref([1, 2, 3, 4, 5]);

const nextDay = () => {
  const val = days.value.shift();
  val !== undefined && days.value.push(val + 5);
};
const previousDay = () => {
  const val = days.value.pop();
  val !== undefined && days.value.unshift(val - 5);
};
</script>

<template>
  <div class="flex flex-col">
    <div class="flex">
      <div @click="previousDay" class="bg-blue-200 p-4">previousDay</div>
      <div @click="nextDay" class="bg-green-200 p-4">nextDay</div>
    </div>
    <div class="bg-red-100 bg-red-200 bg-red-300 bg-red-400 bg-red-500"></div>
    <div class="flex gap-2">
      <div v-for="day in days" :key="day">
        <KeepAlive>
          <component :is="DayColumn" :key="day" :unix-day="day" />
        </KeepAlive>
      </div>
    </div>
  </div>
</template>
