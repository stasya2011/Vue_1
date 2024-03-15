<script setup lang="ts">
import { ref, reactive, onMounted } from 'vue';
import PaginationComponent from './PaginationComponent.vue';

interface IList {
  data: { id: number; title: string }[] | null;
}

let list = reactive<IList>({ data: null });
let currentPage = ref<number>(1);

const fetchData = async () => {
  const response = await fetch(
    `https://jsonplaceholder.typicode.com/todos?_limit=10&_page=${currentPage.value}`
  );
  const json = await response.json();
  list.data = JSON.parse(JSON.stringify(json));
};

const handlePageUpdate = (page: number) => {
  currentPage.value = page;
  fetchData();
};

onMounted(() => {
  setTimeout(() => fetchData(), 3000);
});
</script>

<template>
  <div>
    <ul v-if="list.data">
      <li v-for="el in list.data" :key="el.id">{{ el.title }}</li>
    </ul>
    <div v-else>
      <h3>Loading...</h3>
    </div>
    <div>
      <PaginationComponent :totalPages="10" @update:page="handlePageUpdate" />
    </div>
  </div>
</template>
