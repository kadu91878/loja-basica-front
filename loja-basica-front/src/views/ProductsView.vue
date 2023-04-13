<template>
  <NSpin :show="loading">
    <n-card>
      <template v-for="product in productList">
        <ProductCard :category="product.category" :description="product.description" :title="product.title"
        :image="product.image" :price="product.price"
        />
      </template>
    </n-card>
  </NSpin>
</template>


<script setup lang="ts">
import ProductCard from '../components/ProductCard.vue'
import axios from "axios";
import { onMounted, ref } from "vue";
import type { product } from "../types/product";
import { NSpin, NCard } from "naive-ui";

const productList = ref<product[]>([]);

const loading = ref(false);

const getProduct = async () => {
  try {
    const response = await axios.get("https://fakestoreapi.com/products");
    productList.value = response.data;
    console.log("produtos", productList.value);
  } catch (error) {
    console.error(error);
  }
};

(async () => {
  loading.value = true;
  await getProduct();
  loading.value = false;
})();
// async function getProductList() {
//   loading.value = true;
//   await axios.get("https://fakestoreapi.com/products").then((response) => {
//     productList.value = response.data;
//     loading.value = false;
//   });
// }
</script>