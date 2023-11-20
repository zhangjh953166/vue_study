<script setup>
import { ref } from 'vue'

defineProps(['title'])
const count = ref(0)
</script>

<template>
    <div class="blog-post">
      <h4>{{ title }}</h4>
      <button @click="$emit('enlarge-text')">Enlarge text</button>
    </div>
  </template>