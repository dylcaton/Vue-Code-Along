<template>
  <div style="background-color: aqua; padding: 10px;">
    <h2>This is the Component1 component</h2>
  </div>
</template>

<script setup>
import {
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted
} from 'vue'

console.log('Component1 is setup.')

onBeforeMount(() => {
  console.log('Component1 is before mounted.')
})

onMounted(() => {
  console.log('Component1 is mounted.')
})

onBeforeUpdate(() => {
  console.log('Component1 is before updated.')
})

onUpdated(() => {
  console.log('Component1 is updated.')
})

onBeforeUnmount(() => {
  console.log('Component1 is before unmounted.')
})

onUnmounted(() => {
  console.log('Component1 is unmounted.')
})
</script>