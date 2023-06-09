<template>
  <div id="app">
    <p>O contador está em {{ count }}</p>
    <button v-on:click="count++">Adicionar</button>

    {{ userName }}
  </div>
  
  <div>
    <img :src="image" alt="" srcset="">
  </div>

  <div>
    <ul>
      <template v-for="(user, key) in users" :key="index">
      <li v-if="user.is_admin === 1">
          {{ user.firstName }} | {{ key }}
        </li>
      </template>
    </ul>

  </div>
</template>

<script setup>
import { onMounted, onUpdated, reactive, ref } from 'vue';

const image = 'https://picsum.photos/200/300';

const user = reactive({ firstName: "teste", age: 30 })

const users = reactive([
  {
    id: 1,
    firstName: 'Rodolfo',
    age: 50,
    is_admin: 1
  },
  {
    id: 2,
    firstName: 'Rodolfo',
    age: 89,
    is_admin: 0
  },
  {
    id: 3,
    firstName: 'Rodolfo cAR',
    age: 89,
    is_admin: 1
  },
])

const userName = ref('Rodolfo')
const count = ref(0);
var nome = `rodolfo`
onMounted(() => {
  console.log('Mounted');
  console.log(nome);
})

onUpdated(() => {
  console.log('updated');
})

</script>  