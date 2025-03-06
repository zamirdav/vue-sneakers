<script>
export default {  // option Api увеличение на 1
  data() {
    // метод
    return {
      // возвращает count: 0,
      count: 0,
    }
  },
  methods: {
    //метод что нужно сделать
    increment() {
      //  сам назвал
      this.count++ // просто count++ без this. не работает
    },
  },
}
</script>
<template>
  <!-- <h1>{{ count }}</h1> выдает на экран состояние count -->
  <button @click="increment">+</button>
</template>
