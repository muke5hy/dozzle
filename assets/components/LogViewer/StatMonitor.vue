<template>
  <div class="relative hover:text-secondary" @mouseenter="mouseOver = true" @mouseleave="mouseOver = false">
    <div class="mobile-hidden flex overflow-hidden rounded-sm border border-primary px-px pb-px pt-1">
      <stat-sparkline :data="data" @selected-point="onSelectedPoint"></stat-sparkline>
    </div>
    <div class="inline-flex gap-1 rounded bg-base p-px text-xs lg:absolute lg:-left-0.5 lg:-top-2">
      <div class="font-light uppercase">{{ label }}</div>
      <div class="select-none font-bold">
        {{ mouseOver ? selectedPoint?.value ?? selectedPoint?.y ?? statValue : statValue }}
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
const { data, label, statValue } = defineProps<{ data: Point<unknown>[]; label: string; statValue: string | number }>();

let selectedPoint: Point<unknown> | undefined = $ref();

function onSelectedPoint(point: Point<unknown>) {
  selectedPoint = point;
}

let mouseOver = $ref(false);
</script>
