<template>
  <h1>Message: {{message}}</h1>
  <div style="background-color: orange; padding-left: 10px">
    <ComponentA></ComponentA>
  </div>
</template>

<script setup>
import { ref, provide, readonly } from 'vue';

let message = ref('Hello, Provide/inject!')
import ComponentA from './ComponentA.vue';
function updateMessage() {
  message.value = 'Hello, Provide/inject! Updated.'
}
provide('msg', {message, updateMessage})

let count = ref(0);
provide('read-only-count', readonly(count))

</script>

<style scoped>

</style>