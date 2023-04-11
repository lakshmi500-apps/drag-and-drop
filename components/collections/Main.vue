<template>
  
  <CollectionsList
  :listArray="listArray"
    @addList="openListModal"
  />

  <div v-if="is_modal" :key="render">
    <CollectionsAdd @personsList="personsList" />
  </div>
</template>

<script setup lang="ts">
import {ref,onMounted } from 'vue'

const is_modal = ref(false);
const render = ref(0);
const listArray = ref([]);

onMounted(() => {
  const storedData = localStorage.getItem("details");
  if (storedData) {
    listArray.value = JSON.parse(storedData);
  }
});
// Add data to list
const personsList = (data: any) => {
  console.log("dataa=---->",data)
  listArray.value.push(data);
  localStorage.setItem("details", JSON.stringify(listArray.value));
  is_modal.value = false;
};

//To open modal to add list
const openListModal = () => {
  is_modal.value = true;
  render.value++;
};

</script>