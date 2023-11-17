<script setup>
import { ref } from 'vue'

defineProps(['title'])
const count = ref(0)
</script>

<template>
  <button @click="count++">
    You clicked me {{ count }} times.
  </button>
  <h4>{{ title }}</h4>
</template>