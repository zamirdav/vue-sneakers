<script setup>
import ApDrawertHead from './ApDrawerHead.vue'
import CartItemList from './CartItemList.vue'
</script>

<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70"></div>
  <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
    <ApDrawertHead />

    <CartItemList />

    <div class="flex flex-col gap-4 mt-7">
      <div class="flex -col gap-2">
        <span>Itogo:</span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>12900 r</b>
      </div>
      <div class="flex gap-2">
        <span>Nalog:</span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>900 r</b>
      </div>
      <button
        disabled=""
        class="mt-4 transition bg-lime-500 w-full rounded-xl py-3 text-white disabled hover:bg-lime-700 cursor-pointer"
      >
        Oformit zakaz
      </button>
    </div>
  </div>
</template>
