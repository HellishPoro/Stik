<template>
    <div class="info">
      <div>
        <h1>ЖАКЕТ УДЛИНЕННЫЙ, БЕЛЫЙ</h1>
        <div class="price">8 900 RUB</div>
      </div>
        <div class="sizes">
        <p class="descrip">Размеры: </p>
        <div class="sizes-row">
          <div 
            v-for="size in sizes" 
            :key="size.name" 
            class="size-item"
            :class="{
              active: size.name === activeSize && !size.disabled,
              disabled: size.disabled
            }"
            @click="!size.disabled && (activeSize = size.name)"
          >
            <div class="size-box">{{ size.name }}</div>
            <div class="size-label">{{ size.label }}</div>
          </div>
        </div>
      </div>
  
      <div class="colors colors-container">
        <p class="descrip">Цвет: {{ getColorName(activeColor) }}</p>
        <div class="color-options">
          <span 
            v-for="color in colors" :key="color" 
            :style="{ backgroundColor: color }"
            :class="{ active: color === activeColor }"
            @click="activeColor = color"
          ></span>
        </div>
      </div>
      
      <div class="btn-container">
        <button class="btn">Добавить в корзину</button>
        <button class="fav">
          <Icon icon="mdi:bookmark-outline" width="28" />
        </button>
      </div>
  
      <div class="details-section">
        <div class="detail-item" @click="toggleDetail('description')">
          <div class="detail-header">
            <span>ОПИСАНИЕ</span>
            <Icon :icon="activeDetails.description ? 'mdi:minus' : 'mdi:plus'" width="20" />
          </div>
          <div class="detail-content" v-if="activeDetails.description">
            <p>Элегантный удлинённый жакет из плотной ткани.</p>
          </div>
        </div>
        
        <div class="detail-item" @click="toggleDetail('care')">
          <div class="detail-header">
            <span>СОСТАВ И УХОД</span>
            <Icon :icon="activeDetails.care ? 'mdi:minus' : 'mdi:plus'" width="20" />
          </div>
          <div class="detail-content" v-if="activeDetails.care">
            <p>100% хлопок, машинная стирка 30°C.</p>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { Icon } from '@iconify/vue'
  import { ref } from 'vue'
  
  const sizes = [
    { name: 'XS', label: 'мало', disabled: false },
    { name: 'S', label: '', disabled: false },
    { name: 'M', label: 'подписка', disabled: true }
  ]
  const colors = ['#fff', '#000', '#F9F1DC']
  
  const activeSize = ref('S')
  const activeColor = ref('#fff')
  const activeDetails = ref({
    description: false,
    care: false
  })
  
  const getColorName = (color) => {
    switch(color) {
      case '#fff': return 'Белый';
      case '#000': return 'Чёрный';
      case '#F9F1DC': return 'Бежевый';
      default: return '';
    }
  }
  
  const toggleDetail = (type) => {
    activeDetails.value[type] = !activeDetails.value[type]
  }
  </script>
  
  <style scoped>
  .info {
    display: flex;
    flex-direction: column;
    gap: 20px;
    margin-left: 50px;
    max-width: 400px;
  }
  
  .price,
  h1 {
    font-size: 12px;
    display: flex;
    margin: 5px;
    font-weight: 400;
    line-height: 16px;
  }

  .descrip{
    display: flex;
    font-weight: 400;
    font-size: 10px;
    line-height: 14px;
    margin-bottom: 0;
  }
  
  .sizes {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }
  
  .sizes-row {
    display: flex;
    gap: 16px;
  }
  
  .size-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    cursor: pointer;
    transition: 0.2s;
  }
  
  .size-item.disabled {
    cursor: not-allowed;
    opacity: 0.5;
  }
  
  .size-box {
    width: 60px;
    height: 36px;
    border: 1px solid #333;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 400;
    margin-bottom: 4px;
    transition: 0.2s;
  }
  
  .size-item.active .size-box {
    border-color: #000;
  }
  
  .size-item.disabled .size-box {
    border-color: #ccc;
    color: #ccc;
  }
  
  .size-label {
    font-size: 12px;
    color: #666;
  }
  .size-item.disabled .size-label {
    color: #ccc;
  }
  
  .color-options {
    display: flex;
    align-items: center;
  }
  .colors,
  .sizes {
    flex-direction: column;
    gap: 8px;
  }
  .colors-container{
    width: 119px;
    height: 51px;
  }
  .colors p {
    margin: 0 0 5px;
  }
  .colors span {
    display: inline-block;
    width: 28px;
    height: 27px;
    border: 1px solid #333333;
    margin-right: 8px;
    cursor: pointer;
    position: relative;
  }
  .colors span.active::after {
    content: '';
    position: absolute;
    bottom: -4px;
    left: 0;
    width: 100%;
    height: 1px;
    background-color: #4F4F4F;
  }
  
  .btn-container {
    display: flex;
    gap: 10px;
    margin-top: 30px;
  }
  
  .btn {
    background: black;
    color: white;
    border: none;
    cursor: pointer;
    flex-grow: 1;
    font-size: 11px;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    transition: background 0.2s;
    height: 44px;
    width: 306px;
  }
  
  .btn:hover {
    background: #333;
  }
  
  .fav {
    background: none;
    border: 1px solid #000;
    color: #000;
    width: 44px;
    height: 44px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: all 0.2s;
    padding: 0;
  }
  
  .fav:hover {
    border-color: #999;
  }
  
  .details-section {
    margin-top: 20px;
    border-top: 1px solid #e0e0e0;
    border-bottom: 1px solid #e0e0e0;
  }
  
  .detail-item {
    padding: 16px 0;
    border-bottom: 1px solid #e0e0e0;
  }
  
  .detail-item:last-child {
    border-bottom: none;
  }
  
  .detail-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    cursor: pointer;
    font-weight: 500;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    font-size: 14px;
  }
  
  .detail-content {
    padding-top: 12px;
    color: #666;
    font-size: 14px;
    line-height: 1.5;
  }

  @media (max-width: 768px){
    .price,
    h1{
        font-size: 12px;
        line-height: 16px;
    }
    .info{
        margin-left: 17px;
        margin-right: 17px;
    }
    .btn{
        display: none;
    }
    .fav{
        position: absolute;
        top: 630px;
        left: 331px;
        border: none;
    }
    .btn-container{
        margin: 0;
    }
    .details-section{
        margin-top: 0;
    }
  }
  </style>