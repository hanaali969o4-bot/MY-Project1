<template>
  <nav class="navbar">
    <div class="navbar-container">
      <a class="navbar-brand" href="#">Vue Shop</a>
      
      <div class="navbar-menu">
        <div class="search-bar">
          <form class="search-form" @submit.prevent="handleSearch">
            <input
              class="search-input"
              type="search"
              placeholder="Search products..."
              aria-label="Search"
              v-model="searchQuery"
            >
            <button class="search-button" type="submit">Search</button>
          </form>
        </div>
        
        <div class="cart-icon-wrapper">
          <a class="cart-link" href="#">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" class="bi bi-cart3" viewBox="0 0 16 16">
              <path d="M0 1.5A.5.5 0 0 1 .5 1H2a.5.5 0 0 1 .485.379L2.89 3H14.5a.5.5 0 0 1 .49.598l-1 5a.5.5 0 0 1-.46.402H3.793a.5.5 0 0 1-.49-.402l-1-5A.5.5 0 0 1 2 3H.5a.5.5 0 0 1-.5-.5zM3.102 4l.84 4.474 8.675.249L14.102 4H3.102zM5 12a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm7 0a2 2 0 1 0 0 4 2 2 0 0 0 0-4zm-7 1a1 1 0 1 1 0 2 1 1 0 0 1 0-2zm7 0a1 1 0 1 1 0 2 1 1 0 0 1 0-2z"/>
            </svg>
            <span v-if="!isCartEmpty" class="cart-badge">
              {{ cartCount }}
            </span>
          </a>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, computed, defineProps } from 'vue';

const props = defineProps({
  cartCount: {
    type: Number,
    required: true,
  },
});

const isCartEmpty = computed(() => props.cartCount === 0);
const searchQuery = ref('');

const handleSearch = () => {
  console.log('Searching for:', searchQuery.value);
};
</script>

<style scoped>
.navbar {
  background-color: #6A1B9A; /* لون موف غامق للشريط العلوي */
  padding: 15px 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  color: white;
}

.navbar-container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.navbar-brand {
  color: white;
  font-size: 1.8em;
  font-weight: bold;
  text-decoration: none;
}

.navbar-menu {
  display: flex;
  align-items: center;
  gap: 20px;
}

.search-form {
  display: flex;
}

.search-input {
  padding: 8px 12px;
  border: 1px solid #ddd;
  border-radius: 5px;
  margin-right: 5px;
  width: 200px;
  color: #333; /* لون خط البحث */
}

.search-button {
  background-color: #AB47BC; /* موف متوسط لزر البحث */
  color: white;
  border: none;
  border-radius: 5px;
  padding: 8px 12px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.search-button:hover {
  background-color: #8E24AA; /* موف أغمق عند التمرير */
}

.cart-icon-wrapper {
  position: relative;
}

.cart-link {
  color: white;
  text-decoration: none;
  display: flex;
  align-items: center;
}

.bi-cart3 {
  color: white;
  width: 24px;
  height: 24px;
}

.cart-badge {
  position: absolute;
  top: -8px;
  right: -8px;
  background-color: #D32F2F; /* أحمر زي ما هو عشان يبان واضح */
  color: white;
  border-radius: 50%;
  padding: 3px 7px;
  font-size: 0.8em;
  font-weight: bold;
  line-height: 1;
}
</style>