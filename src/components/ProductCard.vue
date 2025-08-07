<template>
    <div class="card">
      <img :src="image" alt="product" />
      <div class="name">{{ name }}</div>
      <div class="price">{{ price }}</div>
    </div>
  </template>
  
  <script setup>
  defineProps({
    image: String,
    name: String,
    price: String
  })
  </script>
  
  <style scoped>
  .card {
    text-align: center;
  }
  .card img {
    width: 100%;
    height: 444px;
  }
  .price,
  .name{
    display: flex;
    font-weight: 400;
    font-size: 10px;
    line-height: 14px;
    margin-left: 15px;
  }

  @media (max-width: 768px) {
    .card img{
      width: 168px;
      height: 222px;
    }
    .price,
    .name{
      margin-left: 0;
    }
    .price{
      margin-bottom: 10px;
    }
  }
  </style>
  