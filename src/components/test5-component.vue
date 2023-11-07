<script setup>
    import { ref } from 'vue'
    // ref and function
    const count = ref(0)
    function increment(){
        count.value++
    }
    // v-if
    const awesome = ref(true)
    // v-for
    const parentMessage = ref('Parent')
    const items = ref([{ message: 'Foo' }, { message: 'Bar' }])
</script>

<template>
    <button @click="increment">
        {{ count }}
    </button>
    <button @click="awesome = !awesome">Toggle</button>
    <h1 v-if="awesome">Vue is awesome!</h1>
    <h1 v-else>Oh no 😢</h1>
    <li v-for="(item, index) in items">
        {{ parentMessage }} - {{ index }} - {{ item.message }}
    </li>
</template>