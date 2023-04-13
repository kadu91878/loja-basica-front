<template>

    <template v-for="product in data">
        {{  product}}
        
    </template>
</template>
<script lang="ts" setup>
import { onMounted, ref } from 'vue';
// import StoreCardProduct from '../../components/StoreCardProduct/StoreCardProduct.vue'
// import banner from '../../assets/image/banner.svg'
const data = ref({})
const getProduct = () =>{
  fetch('https://fakestoreapi.com/products')
    .then(res=>res.json())
    .then(result =>{
      data.value = result
      console.log("prdocutos", data)
    })
  }
onMounted(() =>{
  getProduct()
})
</script>
