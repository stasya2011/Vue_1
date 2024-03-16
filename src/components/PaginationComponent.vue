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
div {
  display: flex;
  justify-content: space-between;
  max-width: 500px;
  border: 1px solid green;
  border-right: none;
}
button {
  background-color: transparent;
  border: none;
  border-right: 2px solid green;
  text-align: center;
  width: 100%;
}
</style>

<script setup lang="ts">
defineProps({ totalPages: Number });
const emit = defineEmits(['update:page']);
const emitPageUpdate = (page: number) => {
  emit('update:page', page);
};
</script>
