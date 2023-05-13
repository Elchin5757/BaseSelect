<script setup lang="ts">
import BaseSelect from "@/components/BaseSelect.vue";
import { ref, computed } from "vue";
const selected = ref(null);
const selected_2 = ref(1);
const items = [
  { name: "Item 1", value: 1 },
  { name: "Item 2", value: 2 },
  { name: "Item 3", value: 3 },
];

const errorMessage = computed(() => {
  if (selected.value === null) {
    return "Please select an item";
  }
  return null;
});
const errorMessage_2 = computed(() => {
  if (selected_2.value === null) {
    return "Please select an item";
  }
  return null;
});
</script>

<template>
  <div class="flex flex-col items-center justify-center">
    <h1 class="text-3xl font-bold underline">Hello world!</h1>
    <BaseSelect
      v-model="selected"
      :items="items"
      label="Select"
      placeholder="Select"
      :error-message="errorMessage"
      class="w-1/2"
    />
    <BaseSelect
      v-model="selected_2"
      :items="items"
      label="Select"
      placeholder="Select"
      :error-message="errorMessage_2"
      class="w-1/2"
    />
  </div>
</template>
