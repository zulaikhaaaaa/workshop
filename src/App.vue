<script setup>
import {ref, onMounted} from 'vue';
import PocketBase from 'pocketbase';

const pb = new PocketBase('http://127.0.0.1:8090');

const titleVal = ref("");
const data = ref([]);


async function submit() {

  const record = {
    title: titleVal.value, 
    description: "desc" 
  };
  await pb.collection('workshop').create(record);

  data.value.push(record);
}
onMounted (async() =>{
  const result = await pb.collection('workshop').getFullList();

  data.value = result;
})
</script>

<template>
  <input class="bg-red-400 mx-3" v-model="titleVal"/>
  <button class="bg-red-400 text-white px-5 py-2 rounded-lg my-2 mx-3 transition duration-300 hover:bg-red-600" @click="submit">Add</button>

  <ul>
    <li v-for="item in data">{{ item.title }}</li>
  </ul>
</template>

