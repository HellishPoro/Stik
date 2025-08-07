<template>
  <section class="similar">
    <h2 class="header">ПОХОЖИЕ ТОВАРЫ</h2>
    <div class="grid">
      <ProductCard
        v-for="(item, index) in items"
        :key="index"
        :image="item.image"
        :name="item.name"
        :price="item.price"
      />
    </div>
  </section>
</template>

<script setup>
import ProductCard from './ProductCard.vue'

const items = [
  { image: '/src/assets/product/4.png', name: 'Платье с глубоким вырезом, белый', price: '14 900 RUB' },
  { image: '/src/assets/product/5.png', name: 'Жакет двубортный, серо-голубой', price: '8 900 RUB' },
  { image: '/src/assets/product/6.png', name: 'Платье макси с рюшами, белый', price: '10 500 RUB' },
  { image: '/src/assets/product/7.png', name: 'Комбинезон со стойкой, черный', price: '9 500 RUB' },
]
</script>

<style scoped>
.similar {
  margin-top: 80px;
  margin-bottom: 20px;
  padding: 0 16px;
}

.header {
  display: flex;
  font-size: 12px;
  font-weight: 400;
  line-height: 16px;
  margin-bottom: 20px;
}

.grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
}

@media (max-width: 1024px) {
  .grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (max-width: 768px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 11px;
  }
}
</style>