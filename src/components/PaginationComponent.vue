<template>
  <div>
    <button
      v-for="page in totalPages"
      :key="page"
      @click="emitPageUpdate(page)"
    >
      {{ page }}
    </button>
  </div>
</template>

<style scoped>
button {
  background-color: transparent;
  border: 2px solid green;
  border-radius: 15px;
}
</style>

<script setup lang="ts">
defineProps({ totalPages: Number });
const emit = defineEmits(['update:page']);
const emitPageUpdate = (page: number) => {
  emit('update:page', page);
};
</script>
