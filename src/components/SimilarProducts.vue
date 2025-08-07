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
import four from '../assets/product/four.png'
import five from '../assets/product/five.png'
import s from '../assets/product/s.png'
import seven from '../assets/product/seven.png'

const items = [
  { image: four, name: 'ПЛАТЬЕ С V-ОБРАЗНЫМ ВЫРЕЗОМ, БЕЛЫЙ', price: '14 900 RUB' },
  { image: five, name: 'ЖАКЕТ ДВУБОРТНЫЙ, СЕРО-ГОЛУБОЙ', price: '8 900 RUB' },
  { image: s, name: 'ПЛАТЬЕ МАКСИ С ЯРУСАМИ, БЕЛЫЙ', price: '10 500 RUB' },
  { image: seven, name: 'КОМБИНЕЗОН СО СТОЙКОЙ, ЧёРНЫЙ', price: '9 500 RUB' },
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