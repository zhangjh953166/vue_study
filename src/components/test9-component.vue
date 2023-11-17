<script setup>
import { ref } from 'vue'
import ButtonCounter from './ButtonCounter.vue'

const posts = ref([
  { id: 1, title: 'My journey with Vue' },
  { id: 2, title: 'Blogging with Vue' },
  { id: 3, title: 'Why Vue is so fun' }
])
</script>
<template>
    <ButtonCounter
  v-for="post in posts"
  :key="post.id"
  :title="post.title"
 ></ButtonCounter>
</template>