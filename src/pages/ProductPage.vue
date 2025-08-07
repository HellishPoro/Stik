<template>
    <div class="page">
      <Header />
      <main class="product-page">
        <section class="product-main">
          <ProductSlider />
          <ProductInfo />
        </section>
        <SimilarProducts />
      </main>
    </div>
  </template>
  
  <script setup>
    import Header from '../components/Header.vue';
    import ProductInfo from '../components/ProductInfo.vue';
    import ProductSlider from '../components/ProductSlider.vue';
    import SimilarProducts from '../components/SimilarProducts.vue';

  </script>
  
  <style scoped>
  .product-page {
    position: relative;
    bottom: 41px;
    max-width: 1440px;
    margin: 0 auto;
  }
  .product-main {
    display: flex;
    gap: 40px;
    margin-top: 40px;
  }
  @media (max-width: 768px) {
    .product-main {
      flex-direction: column;
    }
  }
  </style>
  