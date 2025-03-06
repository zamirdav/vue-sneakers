// eslint-disable-next-line vue/multi-word-component-names
<template>
  <header class="flex justify-between border-b border-slate-100 px-10 py-8">
    <div class="flex items-center gap-4">
      <img src="/logo.png" alt="logo" class="w-10" />
      <div>
        <h2 class="text-xl font-bold uppercase">Vue Sneakers</h2>
        <p class="text-slate-400">Магазин лучших кроссовок</p>
      </div>
    </div>

    <ul class="flex items-center text-gray-500 gap-3">
      <li class="flex items-center cursor-pointer gap-3 text-gray-500">
        <img src="/cart.svg" alt="cart" />
        <b>1205 руб.</b>
      </li>

      <li class="flex items-center cursor-pointer gap-3 text-gray-500">
        <img src="/heart.svg" alt="cart" />
        <b>закладки</b>
      </li>

      <li class="flex items-center cursor-pointer gap-3 text-gray-500">
        <img src="/profile.svg" alt="cart" />
        <b>Профиль</b>
      </li>
    </ul>
  </header>
</template>
