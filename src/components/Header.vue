<template>
    <header class="header">
      <div class="mobile-left-icons">
        <Icon icon="mdi:magnify" width="20" />
        <Icon icon="mdi:account-outline" width="20" />
      </div>
  
      <div class="logo-container">
        <img :src="logo" alt="stic logo" class="logo" />
      </div>
  
      <div class="icons">
        <button>
          <Icon icon="mdi:magnify" width="28" class="desktop-icon" />
        </button>
        <button>
          <Icon icon="mdi:bookmark-outline" width="28" class="desktop-icon" />
        </button>
        <button>
          <Icon icon="mdi:account-outline" width="28" class="desktop-icon" />
        </button>
        <button>
          <Icon icon="mdi:shopping-outline" class="general-icon" />
        </button>
      </div>
    </header>
  </template>
  
  <script setup>
  import { Icon } from '@iconify/vue'
  import logo from '../assets/product/n.png'
  
  </script>
  
  <style scoped>
  .header {
    max-width: 1440px;
    margin: 0 auto;
    position: relative;
    height: 86px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-direction: row-reverse;
    padding: 0 40px;
  }
  
  .logo-container {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
  }
  
  .logo {
    height: 24px;
    width: 53px;
  }
  
  .icons {
    display: flex;
    gap: 20px;
    color: black;
  }
  
  .mobile-left-icons {
    display: none;
    gap: 20px;
  }
  
  .desktop-icon {
    display: block;
    color: black;
  }

  .general-icon{
    color: black;
    width: 28px;
    height: 28px;
  }

  button{
    background: white;
    border: none;
    cursor: pointer;
  }
  
  @media (max-width: 768px) {
    .header {
        height: 50px;
        padding: 0;
        justify-content: space-between;
        flex-direction: row;
    }
  
    .logo-container {
      position: static;
      left: auto;
      transform: none;
      flex-grow: 1;
      display: flex;
      justify-content: center;
    }
  
    .mobile-left-icons {
      display: flex;
      margin-left: 16px;
      gap: 12px;
    }
  
    .icons {
      gap: 0;
      margin-right: 16px;
    }
  
    .desktop-icon {
      display: none;
    }
    .general-icon{
      width: 20px;
      height: 20px;
    }
  }
  </style>