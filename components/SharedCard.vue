<script lang="ts" setup>
import type { SharedCardOption } from "../shared/card";

defineProps<{
  option: SharedCardOption;
}>();

const svgAttrs = computed(() => {
  const width = 400;
  const height = 600;

  return {
    width,
    height,
  };
});

const containerAttrs = computed(() => {
  const { width, height } = svgAttrs.value;

  const padding = 40;

  return {
    width: width - padding * 2,
    height: height - padding * 2,
    x: padding,
    y: padding,
    rx: 20,
  };
});

const datetimeAttrs = computed(() => {
  const { x, y } = containerAttrs.value;

  return {
    x: x + 20,
    y: y + 20,
  };
});

const titleAttrs = computed(() => {
  const { x, y } = datetimeAttrs.value;

  return {
    x: x,
    y: y + 30,
  };
});
</script>

<template>
  <svg xmlns="http://www.w3.org/2000/svg" v-bind="svgAttrs" class="shared-card">
    <defs>
      <filter id="shadow">
        <feOffset in="SourceGraphic" dx="0" dy="0" />
        <feGaussianBlur stdDeviation="15" />
        <feBlend in="SourceGraphic" in2="blurOut" />
      </filter>
    </defs>

    <rect
      class="content-bg"
      v-bind="containerAttrs"
      filter="url(#shadow)"
    ></rect>
    <text class="datetime" v-bind="datetimeAttrs">
      {{ option.datetime }}
    </text>

    <text class="title" v-bind="titleAttrs">
      {{ option.title }}
    </text>
  </svg>
</template>

<style>
text {
  dominant-baseline: hanging;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.shared-card {
  background: linear-gradient(45deg, rgb(255, 92, 92), rgb(255, 255, 126));
}

.datetime {
  fill: #8c8c8c;
}

.title {
  font-size: 20px;
  font-weight: 500;
}

.content-bg {
  fill: white;
}
</style>
