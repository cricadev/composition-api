<script setup lang="ts">
import { onMounted } from "vue";
import TheWelcome from "@/components/TheWelcome.vue";
onMounted(() => {
  console.log("mounted");
});
</script>

<template>
  <main>
    <TheWelcome />
  </main>
</template>
