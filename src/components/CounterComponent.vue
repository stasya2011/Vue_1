<template>
  <div>
    <h2 class="title">Count: {{ count }}</h2>
    <button @click="inc">INC</button>
    <button @click="dec">DEC</button>
  </div>
</template>

<script setup>
import { ref, onMounted, onUpdated } from 'vue';

onMounted(() => {
  console.log('The component was mounted');
});

onUpdated(() => {
  console.log('updated');
});

let count = ref(0);
const inc = () => (count.value += 1);
const dec = () => count.value--;
</script>

<style>
.title {
  color: green;
}
</style>
