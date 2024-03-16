<template>
  <div>
    {{ age }}
    <input v-model="str" v-bind:placeholder="title" @keyup.enter="fn" />
    ++<slot></slot>++
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
defineProps({ title: String, age: Number });
const str = ref('');

const fn = () => {
  console.log(str.value);
};
</script>
