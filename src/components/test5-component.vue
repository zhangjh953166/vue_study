<script setup>
    import { ref } from 'vue'
    import { watch } from 'vue'
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
    //select
    const selected = ref('A')

    const options = ref([
    { text: 'One', value: 'A' },
    { text: 'Two', value: 'B' },
    { text: 'Three', value: 'C' }
    ])

    //watch
    const question = ref('')
    const answer = ref('Questions usually contain a question mark. ;-)')

    watch(question,async(newQuestion,oldQuestion)=>{
        if (newQuestion.indexOf('?')>-1) {
            answer.value = 'Thinking...'
            try{
                const res = await fetch('https://yesno.wtf/api')
                answer.value = (await res.json()).answer
            } catch (error) {
                answer.value = 'Error! Could not reach the API. ' + error
            }
        }
    })
</script>

<template>
<p>
    <button @click="increment">
        {{ count }}
    </button>
</p>
    <button @click="awesome = !awesome">Toggle</button>
<p>
    <h1 v-if="awesome">Vue is awesome!</h1>
    <h1 v-else>Oh no 😢</h1>
</p>
    <li v-for="(item, index) in items">
        {{ parentMessage }} - {{ index }} - {{ item.message }}
    </li>
<p>
    <select v-model="selected">
        <option v-for="option in options" :value="option.value">
            {{ option.text }}
        </option>
    </select>
    <div>Selected: {{ selected }}</div>
</p>
<p>
    Ask a yes/no question:
    <input v-model="question" />
</p>
<p>{{ answer }}</p>
</template>