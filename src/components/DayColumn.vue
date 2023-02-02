<script lang="ts">
export default {
  name: "CustomName",
  inheritAttrs: false,
  customOptions: {},
};
</script>
<script setup lang="ts">
import { onMounted, ref, onUnmounted } from "vue";
import Draggable from "./Draggable.vue";
const props = defineProps<{ unixDay: number }>();
const columnState = ref(0);

onMounted(() => {
  console.log("column onMounted " + props.unixDay);
});

onUnmounted(() => {
  console.log("column onUnmounted " + props.unixDay);
});
</script>

<template>
  <div
    class="flex flex-col"
    :class="`bg-red-${((Math.abs(props.unixDay) % 5) + 1) * 100}`"
  >
    <div>Day {{ props.unixDay }}</div>
    <div @click="columnState++">cstate {{ columnState }}</div>
    <Draggable :unix-day="props.unixDay" />
  </div>
</template>
