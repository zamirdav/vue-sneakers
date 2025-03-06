<script setup> // без setup не исполняются компоненты
import { onMounted, ref, reactive, watch } from 'vue'
import axios from 'axios'
import Header from './components/ApHeader.vue'
import CardList from './components/CardList.vue'
import Drawer from './components/ApDrawer.vue'

const items = ref([])

const filters = reactive({
  sortBy: 'title',
  searchQuery: '',
})

const onChangeSelect = event => {
  filters.sortBy = event.target.value
}

const onChangeSearchInput = event => {
  //запрашивает список товаров
  filters.searchQuery = event.target.value
}

const fetchFavorites = async () => {
  //запрашивает список закладок
  try {
    const { data: favorites } = await axios.get(
      `https://ad4a733e44ba7164.mokky.dev/favorites`,
    )

    items.value = items.value.map(item => {
      const favorite = favorites.find(
        (favorites.id === favorite.parentId) === item.id,

      )
      if (!favorite) {
        return item
      }
      return {
        ...item,
        isFavorite: true,
        favoriteId: favorite.id,
      }
    })
    console.log(items)
  } catch (err) {
    console.log(err)
  }
}

const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy,
    }

    if (filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`
    }

    const { data } = await axios.get(
      `https://ad4a733e44ba7164.mokky.dev/items`,
      {
        params,
      },
    )

    items.value = data.map(obj => ({
      //список всех обьектов
      ...obj,
      isFavorite: false,
      isAdded: false,
    }))
  } catch (err) {
    console.log(err)
  }
}

onMounted(async () => {
  await fetchItems()
  await fetchFavorites()
})
watch(filters, fetchItems)
</script>

<template>
  <!--<Drawer /> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">
    <Header />
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold wb-8">Все кроссовки</h2>
        <div class="flex gap-4">
          <select
            @change="onChangeSelect"
            class="py-2 px-3 border rounded-md outline-none"
          >
            <option value="name">PO NAZVANIU</option>
            <option value="price">PO SENE DESH</option>
            <option value="-price">PO SENE DOROG</option>
          </select>
          <div class="relative">
            <img class="absolute lef-4 top-3" src="/search.svg" />
            <input
              @input="onChangeSearchInput"
              class="border border-gray-200 rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-400"
              type="text"
              placeholder="POISK..."
            />
          </div>
        </div>
      </div>
      <div class="mt-10">
        <CardList :items="items" />
      </div>
    </div>
  </div>
</template>
