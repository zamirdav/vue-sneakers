<script setup>
import Card from './ApCard.vue'
defineProps({
  items: Array,
})
const onClickAdd = () => {
  alert('Добавить')
}
</script>
<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :title="item.title"
      :price="item.price"
      :imageUrl="item.imageUrl"
      :onClickAdd="onClickAdd"
    />
  </div>
</template>
