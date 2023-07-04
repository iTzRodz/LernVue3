<template>
  <h1>Lista de users</h1>
  <!-- <ul>
    <li v-for="user in users.user" :key="user.id"> {{ user }}</li>
  </ul> -->

  <img :src="imageSrc" alt="" class="my-default-class" :class="{'my-class':is_admin, 'my-other-class': !is_admin}">
  <ul>
    <!-- Caso eu precise fazer um for com if eu não posso colocar o for e IF na tag li. Eu coloco o for no template e a condição dentro do LI -->
    <template v-for="user in users.user" :key="user.id">
      <li v-if="user.is_admin === 1"> {{ user.firstName }}</li>
    </template>
  </ul>
</template>

<script setup>
import { onMounted, onUpdated, reactive, ref } from 'vue';
import http from '@/services/http.js';

const users = reactive({user: []})

const imageSrc = ref('https://picsum.photos/200/300')
const is_admin = ref(true)

const listUsers = async () => {
  try {
    const { data } = await http.get('/users')
    users.user = data
    console.log(users.user);
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

<style scoped>
.my-class {
  border: 4px solid red;
}
.my-other-class {
  border: 4px solid blue;
}
</style>