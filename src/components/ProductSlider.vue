<template>
  <div class="slider">
    <div class="desktop-slider">
      <div class="thumbs">
        <img
          v-for="(image, index) in images"
          :key="index"
          :src="image"
          :class="{ active: index === activeIndex }"
          @click="activeIndex = index"
        />
      </div>
      <div class="main-image">
        <img :src="images[activeIndex]" alt="Product image" />
        <button class="arrow left" @click="prev">
          <Icon icon="mdi:chevron-left" width="24" />
        </button>
        <button class="arrow right" @click="next">
          <Icon icon="mdi:chevron-right" width="24" />
        </button>
      </div>
    </div>

    <div class="mobile-slider">
      <swiper
        :slides-per-view="1"
        :loop="true"
        :navigation="{
          nextEl: '.mobile-next',
          prevEl: '.mobile-prev'
        }"
        :pagination="{ clickable: true }"
        class="mobile-swiper"
      >
        <swiper-slide v-for="(image, index) in images" :key="index">
          <img :src="image" alt="Product image" />
        </swiper-slide>
        
        <div class="mobile-navigation">
          <button class="arrow mobile-prev">
            <Icon icon="mdi:chevron-left" width="24" />
          </button>
          <button class="arrow mobile-next">
            <Icon icon="mdi:chevron-right" width="24" />
          </button>
        </div>
      </swiper>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { Swiper, SwiperSlide } from 'swiper/vue'
import SwiperCore, { Navigation, Pagination } from 'swiper'
import 'swiper/css'
import 'swiper/css/navigation'
import 'swiper/css/pagination'
import { Icon } from '@iconify/vue'
import one from '../assets/product/one.png'
import two from '../assets/product/two.png'
import three from '../assets/product/three.png'

SwiperCore.use([Navigation, Pagination])

const images = [
  one,
  two,
  three,
]
const activeIndex = ref(0)

function next() {
  activeIndex.value = (activeIndex.value + 1) % images.length
}

function prev() {
  activeIndex.value = (activeIndex.value - 1 + images.length) % images.length
}
</script>

<style scoped>
.slider {
  display: flex;
  flex-direction: column;
}

.desktop-slider {
  display: flex;
  gap: 16px;
  margin-left: 150px;
}

.thumbs {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.thumbs img {
  width: 70px;
  height: 70px;
  object-fit: cover;
  cursor: pointer;
  border: 1px solid #eee;
}

.thumbs img.active {
  border: 2px solid black;
}

.main-image {
  position: relative;
  width: 518px;
}

.main-image img {
  width: 100%;
  height: auto;
  display: block;
}

.arrow {
  width: 32px;
  height: 32px;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: white;
  border-radius: 50%;
  border: none;
  cursor: pointer;
  opacity: 0.7;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 10;
  color: black;
}

.arrow:hover {
  opacity: 1;
}

.arrow.left {
  left: 10px;
}

.arrow.right {
  right: 10px;
}

.mobile-slider {
  display: none;
  width: 100%;
  max-width: 375px;
  margin: 0 auto;
  position: relative;
}

.mobile-swiper {
  width: 100%;
  height: 617px;
  position: relative;
}

.mobile-swiper img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.mobile-navigation {
  position: absolute;
  top: 50%;
  left: 0;
  right: 0;
  transform: translateY(-50%);
  display: flex;
  justify-content: space-between;
  pointer-events: none;
  z-index: 10;
  padding: 0 16px;
}

.mobile-navigation .arrow {
  position: static;
  transform: none;
  pointer-events: auto;
}

.mobile-prev {
  left: 16px;
}

.mobile-next {
  right: 16px;
}

:deep(.swiper-pagination-bullet) {
  background: white; 
  opacity: 0.5;      
  transition: opacity 0.3s ease; 
}

:deep(.swiper-pagination-bullet-active) {
  opacity: 1;     
}

@media (max-width: 768px) {
  .desktop-slider {
    display: none;
  }
  
  .mobile-slider {
    display: block;
  }
}
</style>