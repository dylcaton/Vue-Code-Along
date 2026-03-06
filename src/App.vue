<template>
  <h1>{{ message }}</h1>

  <div class="card">
    <h1>Scenario 3: Watch a "ref(object)"</h1>
    <h2>Name: {{ wizard2.name }}</h2>
    <h2>Wand: {{ wizard2.wand }}</h2>
    
    <button @click="wizard2.name = wizard2.name.toUpperCase()">
      Change name to upper case
    </button>
    
    <button @click="wizard2.wand.core = 'Phoenix feather'">
      Change wand core
    </button>
    
    <button @click="changeWizard">Change wizard</button>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

let message = ref('Hello, Watchers!')

// Scenario 3: Watch a ref(object)
let wizard2 = ref({
  id: 1003,
  name: 'Ron Weasley',
  house: 'Gryffindor',
  age: 17,
  wand: {
    core: 'Unicorn hair',
    wood: 'Willow'
  }
})

function changeWizard() {
  wizard2.value = {
    id: 1002,
    name: 'Hermione Granger',
    house: 'Gryffindor',
    age: 17,
    wand: {
      core: 'Dragon heartstring',
      wood: 'Vine'
    }
  }
}

watch(wizard2, (newValue, oldValue) => {
  console.log('Watch a ref(object): wizard2 changes', newValue, oldValue)
}, { deep: true })

</script>

<style scoped>
.card {
  background-color: purple;
  color: white;
  padding: 20px 10px;
  margin-bottom: 10px;
}
</style>