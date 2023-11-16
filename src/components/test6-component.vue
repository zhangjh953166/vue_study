<script setup>
import { ref,onMounted } from 'vue'
const input = ref(null)
const list = ref([
    'a','b','c'
])
const itemRefs = ref([])
onMounted(() => {
    input.value.focus()
    console.log('a',itemRefs.value)
})

</script>
<template>
<p>
    <input ref="input" />
</p>
<ul>
    <li v-for="item in list" ref="itemRefs">
      {{ item }}
    </li>
</ul>
</template>