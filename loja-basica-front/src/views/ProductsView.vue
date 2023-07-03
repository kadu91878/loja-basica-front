<template>
  <NSpin :show="loading">
    <input type="text" v-model="keyword" placeholder="Enter keyword">
    <button @click="filterProducts(keyword)">Filter</button>

    <div v-for="product in filteredProducts" :key="product.id">
      <ProductCard
        :category="product.category"
        :description="product.description"
        :title="product.title"
        :image="product.image"
        :price="product.price"
      />
    </div>
  </NSpin>
</template>

<script setup lang="ts">
import ProductCard from '../components/ProductCard.vue';
import axios from 'axios';
import { onMounted, ref } from 'vue';
import type { product } from '../types/product';
import { NSpin } from 'naive-ui';

let productList = ref<product[]>([]);
const loading = ref(false);
let filteredProducts = ref<product[]>([]);

const getProduct = async () => {
  try {
    const response = await axios.get('https://fakestoreapi.com/products');
    productList.value = response.data;
    filteredProducts.value = productList.value;
    console.log('produtos', productList.value);
  } catch (error) {
    console.error(error);
  }
};

onMounted(async () => {
  loading.value = true;
  await getProduct();
  loading.value = false;
});

function filterProducts(keyword) {
  const filtered = productList.value.filter((product) => {
    for (const key in product) {
      const value = product[key];
      if (value.toString().includes(keyword)) {
        return true;
      }
    }
    return false;
  });
  filteredProducts.value = filtered;
}
</script>
