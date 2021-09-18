<template>
  <div>{{ count }} ({{ nextValue }})</div>
  <button type="button" @click="onPlusButtonClick">Clicl Me!</button>
</template>

<script setup lang="ts">
import { computed } from "vue";

// eslint-disable-next-line no-undef
const props = defineProps({
  count: {
    type: Number,
    required: true,
  },
});

// eslint-disable-next-line no-undef
const emits = defineEmits({
  "update:count": (nextValue: number) => nextValue > 2,
});

const nextValue = computed(() => props.count + 1);

function onPlusButtonClick() {
  emits("update:count", nextValue.value);
}
</script>
