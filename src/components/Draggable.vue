<script setup lang="ts">
import { onMounted, onUnmounted, ref } from "vue";

const props = defineProps<{ unixDay: number }>();

const draggableState = ref(0);

onMounted(() => {
  console.log("draggable onMounted " + props.unixDay);
});

onUnmounted(() => {
  console.log("draggable onUnmounted " + props.unixDay);
});
</script>

<template>
  <div @click="draggableState++">dstate {{ draggableState }}</div>
</template>
