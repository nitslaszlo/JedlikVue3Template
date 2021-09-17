<template>
  <div>{{ props.count }} ({{ nextValue }})</div>
  <button type="button" @click="onPlusButtonClick">Clicl Me!</button>
</template>

<script setup lang="ts">
import { computed, defineProps, defineEmits } from "vue";

const props = defineProps<{
  count: number;
}>();

const emits = defineEmits({
  "update:count": (nextValue: number) => nextValue > 2,
});

const nextValue = computed(() => props.count + 1);

function onPlusButtonClick() {
  emits("update:count", nextValue.value);
}
</script>
