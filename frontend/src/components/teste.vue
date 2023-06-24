<template>
  <h1>Lista de users</h1>
  <ul>
    <li v-for="user in users.user" :key="user.id"> {{ user }}</li>
  </ul>
  {{ users }}
</template>

<script setup>
import { onMounted, onUpdated, reactive, ref } from 'vue';
import http from '@/services/http.js';

const users = reactive({user: []})



const listUsers = async () => {
  try {
    const { data } = await http.get('api/users')
    users.user = data
    console.log(data);
    console.log(users);
  } catch (error) {
    console.log(error);
  }
}

onMounted( async() => {
  await listUsers();

})



</script>  