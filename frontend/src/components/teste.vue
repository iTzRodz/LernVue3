<template>
<div id="app">
    <button @click="increment">Clique aqui para adicionar 1</button>
    <p>O contador está em {{ count }}</p>
  </div>
</template>
<script>
export default {
    data() {
      return {
        count: 0
      }
    },
    methods: {
      increment() {
        this.count++
      }
    }
  }
  