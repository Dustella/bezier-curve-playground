<script setup lang="ts">
import { useDraggable } from '@vueuse/core'
import { onMounted, reactive, ref } from 'vue'

const points = reactive([
  { x: 10, y: 400 },
  { x: 120, y: 700 },
  { x: 200, y: 600 },
  { x: 300, y: 400 },
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
  <div
    ref="circle1" :style="style1"
    class="fixed w-4 h-4 bg-blue-500 rounded-full z-200 translate-x--1/2 translate-y--1/2"
  />
  <div
    ref="circle2" :style="style2"
    class="fixed w-4 h-4 bg-blue-500 rounded-full z-200 translate-x--1/2 translate-y--1/2"
  />    <div
    ref="circle3" :style="style3"
    class="fixed w-4 h-4 bg-blue-500 rounded-full z-200 translate-x--1/2 translate-y--1/2"
  />    <div
    ref="circle4" :style="style4"
    class="fixed w-4 h-4 bg-blue-500 rounded-full z-200 translate-x--1/2 translate-y--1/2"
  />
  <!-- create four circles -->
  <svg
    class="fixed inset-0 z-0 bg-transparent h-full w-full"
    view-box="0 0 200 200"

    xmlns="http://www.w3.org/2000/svg"
  >
    <!-- create a bezier curve -->
    <!-- create binding with reactive 'points' -->
    <path
      :d="`M${x1} ${y1} C ${x2} ${y2} ${x3} ${y3} ${x4} ${y4}`"
      stroke="black"
      fill="transparent"
    /></svg>
  <!-- use svg to draw two lines linking xy1 xy2 and xy3 xy4 -->
  <svg
    class="fixed inset-0 z--1 bg-white h-full w-full"
  >
    <line
      :x1="x1" :y1="y1" :x2="x2" :y2="y2"
      stroke="blue"

      fill="transparent"
    />
    <line
      :x1="x3" :y1="y3" :x2="x4" :y2="y4"
      stroke="blue"

      fill="transparent"
    />

  </svg>

  <div class="top-0 fixed inset-x-0 user-select-none">
    <h2>
      just a demo for bezier curve
    </h2>
    <p>
      due to some issues, touch screen will not work properly
      <br>
      plase use mouse to drag the points
    </p>
    x1  {{ x1 }} y1 {{ y1 }}<br>
    x2  {{ x2 }} y2 {{ y2 }}<br>
    x3  {{ x3 }} y3 {{ y3 }}<br>
    x4  {{ x4 }} y4 {{ y4 }}<br>
    <p>Dustella, under AGPL 3.0, <a href="https://github.com/Dustella/bezier-curve-playground">Github</a> </p>
  </div>
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
