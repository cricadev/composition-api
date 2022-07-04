<template lang="">
  <div class="text-center">
    <button
      class="bg-green-500 py-4 px-8 rounded-3xl text-2xl text-black outline-dashed outline-2 outline-green-50"
      @click="toggle"
    >
      modal
    </button>
    <teleport to="header">
      <div v-show="show" class="modal">
        <h1 class="text-4xl text-orange-500 my-4">Title</h1>
        <p class="text-xl text-orange-200 my-4">Lorem, ipsum dolor.</p>
        <button
          class="bg-green-500 py-4 px-8 rounded-3xl text-2xl text-black outline-dashed outline-2 outline-green-50"
          @click="toggle"
        >
          Close
        </button>
      </div>
    </teleport>
  </div>
</template>
<script lang="ts" setup>
import { ref } from "vue";
const show = ref(true);
const toggle = () => (show.value = !show.value);
</script>
<style lang=""></style>
