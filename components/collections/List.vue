<template>
  <div>
    <button class="relative inline-flex items-right rounded-md  text-sm font-semibold" @click="addList">Add New List</button>
    <div class="mt-6 flow-root drop-zone">
      <ul role="list" class="-my-5 divide-y divide-gray-200">
        <li v-for="(person,index) in listArray" :key="index" class="py-4" >
         <!-- <draggable v-model="meals" tag="ul" group="group1" > 
     <template #item="{ element: meals }">
      <li>{{ meals}}</li> 
    </template> 
  </draggable>  -->
  
          <div class="flex items-center space-x-4">
                    
            <div class="min-w-0 flex-1 drag-el" draggable="true">
              <p class="truncate text-sm font-medium text-gray-900">{{ person.name }}</p>
              <p class="truncate text-sm text-gray-500">{{ '@' + person.designation }}</p>
            </div>
      
          </div>
        </li>

      </ul>
    </div>
  
  </div>
</template>

<script setup lang="ts">
import { reactive,ref } from 'vue';
// import draggable from 'vuedraggable';
const meals = ref([
  'Hamburger',
  'Pizza',
  'Spaghetti',
  'Tacos',
  'Teriyaki Chicken',
]);

const people = [
  {
    name: 'Leonard Krasner',
    designation: 'leonardkrasner',
    imageUrl:
      'https://images.unsplash.com/photo-1519345182560-3f2917c472ef?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80',
  },
  {
    name: 'Floyd Miles',
    designation: 'floydmiles',
    imageUrl:
      'https://images.unsplash.com/photo-1463453091185-61582044d556?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80',
  },
  
]
//Defining emit
  const emit = defineEmits([
  "addList",
  
]);
//Defining props
const props=defineProps({
  listArray:Array
})
let data=reactive([])
data=props.listArray;
console.log("data=====",data)

const addList = () => {
  emit("addList");
  
};


</script>
<style scoped>
.drop-zone{
  width:100%;
  margin: 25px auto;
  background-color: aliceblue;
  padding: auto;
  min-height: 5px;
}
.drag-el{
  color: aqua;
  padding: 5px;
  margin-bottom: auto;

}
</style>