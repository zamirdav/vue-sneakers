<script setup> // пример Composition API: setup()
import { ref } from 'vue' // реактивный подход
const count = ref(0)
function increment() {
  count.value++ // count. без value не работает
  console.log(count)
}
//function updateCount(event) {
//  count.value = Number(event.target.value)
//}
</script>

<template>
  <h1>{{ count }}</h1>
  <button @click="increment">+</button>
  <input v-model="count" />
</template>
