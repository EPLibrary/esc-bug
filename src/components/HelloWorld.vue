<template>
  <div class="hello">
    <button @click="open = !open" class="bg-blue-400 px-4 py-2 rounded shadow">Show Palette</button>
    <AppPalette :open="open" @update-model-value="(value) => {open = value}" />
  </div>
</template>

<script setup>

import AppPalette from "@/components/AppPalette";
import {ref} from "vue";
let open = ref(true);
</script>
