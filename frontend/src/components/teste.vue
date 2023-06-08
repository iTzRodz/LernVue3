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
        count: 0,
        interval: ''
      }
    },
    mounted() {
      this.interval = setInterval(() => {
        console.log(`mounted`);
      }, 1000)
    },
    unmounted() {
      clearInterval(this.interval)
    },
    methods: {
      increment() {
        this.count++
      }
    }
}
</script>
