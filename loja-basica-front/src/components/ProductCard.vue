<template>
  <n-card>
    <n-image :src="image" alt="Imagem do produto" width="200" height="200" />
    <div class="product-info">
      <div class="product-name">{{ name }}</div>
      <div class="product-category">{{ category }}</div>
      <div class="product-description">{{ description }}</div>
      <div class="product-price">{{ price }}</div>
    </div>
  </n-card>
</template>


  <script lang="ts" setup>
import { defineProps } from "vue";

import { NCard, NImage } from "naive-ui";

defineProps(["name", "category", "description", "price", "image"]);
</script>

<style scoped>
.product-card {
  display: flex;
  align-items: center;
  padding: 10px;
  margin-bottom: 20px;
  box-shadow: 0px 1px 3px rgba(0, 0, 0, 0.3);
  border-radius: 5px;
}

.product-image {
    display: flex;
  width: 15px;
  height: 20px;
  margin-right: 20px;
}
img {
    width: 50%;
    height: 50%;
    display: flex;
    padding: 10px;;
  }

.product-info {
  display: flex;
  flex-direction: column;
}

.product-name {
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 5px;
}

.product-category {
  font-size: 14px;
  margin-bottom: 5px;
  color: #666;
}

.product-description {
  font-size: 14px;
  margin-bottom: 10px;
  color: #666;
}

.product-price {
  font-size: 18px;
  font-weight: bold;
  color: #00c;
}
</style>
  