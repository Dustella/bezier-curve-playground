<script setup lang="ts">
import { useDraggable } from '@vueuse/core'
import { onMounted, reactive, ref } from 'vue'

const points = reactive([
  { x: 0, y: 0 },
  { x: 20, y: 100 },
  { x: 100, y: 10 },
  { x: 100, y: 100 },
])

const circle1 = ref<HTMLElement>()
const circle2 = ref<HTMLElement>()
const circle3 = ref<HTMLElement>()
const circle4 = ref<HTMLElement>()

const { x: x1, y: y1, style: style1 } = useDraggable(circle1, { initialValue: points[0] })
const { x: x2, y: y2, style: style2 } = useDraggable(circle2, { initialValue: points[1] })
const { x: x3, y: y3, style: style3 } = useDraggable(circle3, { initialValue: points[2] })
const { x: x4, y: y4, style: style4 } = useDraggable(circle4, { initialValue: points[3] })

onMounted(() => {
})
</script>

<template>
  <h1 class="">
    test
  </h1>
  <div class="border-2 h-100  relative">
    <!-- create four circles -->
    <div
      ref="circle1" :style="style1"
      class="absolute w-8 h-8 bg-blue-500 rounded-full z-200"
    />
    <div
      ref="circle2" :style="style2"
      class="absolute w-8 h-8 bg-blue-500 rounded-full z-200"
    />    <div
      ref="circle3" :style="style3"
      class="absolute w-8 h-8 bg-blue-500 rounded-full z-200"
    />    <div
      ref="circle4" :style="style4"
      class="absolute w-8 h-8 bg-blue-500 rounded-full z-200"
    />
    <svg
      class="absolute inset-0 z--1"
      viewBox="0 0 200 200"
      xmlns="http://www.w3.org/2000/svg"
    >
      <!-- create a bezier curve -->
      <!-- create binding with reactive 'points' -->
      <path
        :d="`M${points[0].x} ${points[0].y} C ${points[1].x} ${points[1].y}, ${points[2].x} ${points[2].y}, ${points[3].x} ${points[3].y}`"
        stroke="black"
        fill="transparent"
      /></svg>
  </div>
  {{ points }}
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
