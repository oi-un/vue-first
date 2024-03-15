<script setup>
import { ref } from 'vue';

  const title = ref('상품목록..')
  const products_simple = ref(['아이폰','갤럭시','아이패드','갤럭시탭']);
  const products = ref([
    {
      productId: '001',
      title: 'iphone',
      price: 1200,
      discountRate: 15,
      isRocket: true,
      stock: 5
    },
    {
      productId: '0014',
      title: 'Galaxy23',
      price: 1300,
      discountRate: 25,
      isRocket: true,
      stock: 12
    },
    {
      productId: '0023',
      title: 'ShaomiPhone',
      price: 800,
      discountRate: 34,
      isRocket: false,
      stock: 0
    }
  ])
  const copyright = ref('Copyright 2024 Vue.js')
  const imgSrc = 'https://w7.pngwing.com/pngs/854/555/png-transparent-vue-js-hd-logo-thumbnail.png'
  const imgWidth = 100;

  const typeText = ref('');
  const checkboxChecked = ref(true);

  function buttonClicked(){
    alert('hi button clicked')
  }
  function greetButtonClicked(){
    console.log('hi button clicked')
  }
</script>

<template>
  <h1>안녕 뷰 안녕 에반 유</h1>
  <hr>
  <img :src="imgSrc" :width="imgWidth" />
  <button @click="buttonClicked">눌러주세요</button>
  <button @click="greetButtonClicked">버튼1</button>

  <br><br>
  양방향 테스트 : <input type="text" v-model="typeText">
  {{ typeText }}
  <br>
  체크박스 : <input type="checkbox" v-model="checkboxChecked">
  {{ checkboxChecked }}

  <h3>{{title}}</h3>
  <ul>
    <li v-for="product in products" :key="product.productId">
      <span v-if="product.stock">
        {{ product.title }} - 
        ${{ product.price }} 
        ({{ product.price - (product.price * (product.discountRate / 100)) }}): 
        {{ product.isRocket ? '로켓배송' : '3일 후에 받아요' }}
      </span>
      <span v-else>{{ product.title }} - 재고없음</span>
    </li>
  </ul>
  <h3>{{copyright}}</h3>
</template>

<style scoped>
  h1{color:skyblue}
</style>
