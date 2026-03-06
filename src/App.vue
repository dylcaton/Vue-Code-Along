<template>
  <h1>{{ message }}</h1>

  <div class="card">
    <h1>Scenario 2: Watch a property in a "ref(object)"</h1>
    <h2>Name: {{ wizard1.name }}</h2>
    <h2>Wand: {{ wizard1.wand }}</h2>
    <button @click="wizard1.name = wizard1.name.toUpperCase()">Change name to uppercase</button>
    <button @click ="changeWizard1Wand">Change wand</button>
    <button @click="wizard1.wand.core='Unicorn hair'">Change wand core</button>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

let message = ref('Hello, Watchers!')

// Scenario 2: Watch a property in a ref(object)
let wizard1 = ref({
  id: 1001,
  name: 'Harry Potter',
  house: 'Gryffindor',
  age: 17,
  wand: {
    core: 'Phoenix feather',
    wood: 'Holly'
  }
})

function changeWizard1Wand() {
  wizard1.value.wand = {
    core: 'Dragon heartstring',
    wood: 'Vine'
  }
}

watch(
  () => wizard1.value.name,
  (newValue, oldValue)=> {
    console.log('Watch a property in a ref(object): wizard1 name changes', newValue)
  })

watch(()=> wizard1.value.wand,
(newValue, oldValue) => {
  console.log('Watch a property in a ref(object): wizard1 wand changes', newValue, oldValue),
  {deep:true}
})

watch(()=> wizard1.value.wand.core,
(newValue, oldValue) => {
  console.log('Watch a property in a ref(object): wizard1 wand core changes', newValue, oldValue)
})
</script>

<style scoped>
.card {
  background-color: purple;
  color: white;
  padding: 20px 10px;
  margin-bottom: 10px;
}
</style>