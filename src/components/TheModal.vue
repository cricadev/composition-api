<template lang="">
  <div class="text-center">
    <button
      class="px-8 py-4 text-2xl text-black bg-green-500 rounded-3xl outline-dashed outline-2 outline-green-50"
      @click="toggle"
      :disabled="show"
    >
      modal
    </button>
    <teleport to="header" class="text-center">
      <div v-show="show" class="modal">
        <h1 class="my-4 text-4xl text-orange-500">Title</h1>
        <p class="my-4 text-xl text-orange-200">
          {{ fullName }} {{ attrs.something }} username: {{ username.value }}
        </p>
        <input
          type="text"
          class="text-black"
          v-model="username"
          @input="change"
        />
        <button
          class="px-8 py-4 text-2xl text-black bg-green-500 rounded-3xl outline-dashed outline-2 outline-green-50"
          @click="toggle"
          ref="btn"
        >
          Close
        </button>
      </div>
    </teleport>
  </div>
</template>
<script lang="ts" setup>
import { ref, toRefs, computed, useAttrs, inject, watch } from "vue";
const show = ref(true);
const btn = ref(null);
console.log(btn.value);
watch(btn, (valor) => console.log(valor));
const toggle = () => (show.value = !show.value);
const props = defineProps({
  firstName: String,
  lastName: String,
});
const fullName = computed(() => {
  return `${props.firstName} ${props.lastName}`;
});
toRefs(fullName);
const attrs = useAttrs();
console.log(attrs);

let username = inject("Username");
const change = function (e: any) {
  username = e.target.value;
  console.log(username);
};
</script>
<style lang=""></style>
