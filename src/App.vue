<script setup>
import { ref, reactive, computed } from 'vue'
import Chip from './components/Chip.vue'
import Card from './components/Card.vue'

const keyword = ref('')

const categories = ref([
  'All Menu',
  'Coffee',
  'Fast Food',
  'Noodles',
  'Chicken',
  'Snack',
  'Western',
  'Thai',
  'Chinese'
])

const menus = reactive([
  {
    name: 'Nasi Brongkos Ayam Kampung dan telur',
    price: 'Rp 32.000'
  },
  {
    name: 'Sate Ayam',
    price: 'Rp 24.000'
  },
  {
    name: 'Sate Kambing',
    price: 'Rp 28.000'
  },
  {
    name: 'Steak Tenderloin',
    price: 'Rp 65.000'
  },
  {
    name: 'Kentang Goreng',
    price: 'Rp 15.000'
  },
  {
    name: 'Otak-otak',
    price: 'Rp 15.000'
  },
  {
    name: 'Kopi Tubruk',
    price: 'Rp 25.000'
  },
  {
    name: 'Kopi V60',
    price: 'Rp 30.000'
  },
])

const filteredMenu = computed(() => {
  if (keyword.value) {
    return menus.filter((item) => {
      return keyword.value
        .toLowerCase()
        .split(" ")
        .every((v) => item.name.toLowerCase().includes(v));
      });
    } else {
      return menus;
    }
});
</script>

<template>
  <div class="flex flex-col items-center">
    <div class="container max-w-md">
      <div class="flex flex-col bg-black p-4 gap-4">
        <div class="flex justify-between text-white">
          <span class="font-bold text-lg">Olsera</span>
          <span>Icon</span>
        </div>
        <input class="rounded-full h-8 bg-white py-1 px-3" type="text" placeholder="Search" v-model="keyword" />
        <div class="flex justify-between text-white">
          <span class="font-bold text-xl">Categories</span>
          <span>See All</span>
        </div>
        <div class="flex overflow-scroll gap-2">
          <Chip v-for="category in categories" :text="category" />
        </div>
      </div>
      <div class="container p-2">
        <div class="flex justify-between py-4">
          <span class="font-bold text-2xl">Recomendation</span>
          <span>See All</span>
        </div>
        <div class="grid grid-cols-2 gap-4 mt-2">
          <Card v-for="menu in filteredMenu" :name="menu.name" :price="menu.price" />
        </div>
      </div>
    </div>
  </div>
</template>
