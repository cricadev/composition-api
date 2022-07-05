<script setup lang="ts">
import { onMounted, ref, reactive, watch, computed } from "vue";
import TheWelcome from "@/components/TheWelcome.vue";
const text = ref("hello vue");
const firstName = ref("Cristian");
const lastName = ref("Casallas");
const counter = ref(0);
const obj = reactive({
  counter: 0,
});

setInterval(() => counter.value++, 1000);
setInterval(() => obj.counter++, 1000);

watch(
  () => obj.counter,
  (value, old) => {
    console.log(value, old);
  }
);
const fullName = computed(() => {
  return `${firstName.value} ${lastName.value}`;
});
onMounted(() => {
  console.log("mounted");
});
</script>

<template>
  <main>
    <p>{{ text }} {{ counter }} {{ obj.counter }} {{ fullName }}</p>

    <TheWelcome />
  </main>
</template>
