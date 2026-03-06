<template>
  <h1>{{ message }}</h1>

  <div class="card">
    <h1>Scenario 1: Watch a "ref(primitive value)"</h1>
    <h2>Number: {{ number }}</h2>
    <button @click="number++">Increment number by 1</button>
  </div>
</template>

<script setup>
import { ref,watch } from 'vue'
gi
let message = ref('Hello, Watchers!')

// Scenario 1: Watch a ref(primitive value), this is a comm
let number = ref(1)

let stopWatch = watch(number, (newValue, oldValue) => {
  console.log('Watch a ref(primitive value): number changes', newValue, oldValue);
}, {immediate: true})

if (newValue>5) {
  stopWatch();
}
</script>

<style scoped>
.card {
  background-color: purple;
  color: white;
  padding: 20px 10px;
  margin-bottom: 10px;
}
</style>