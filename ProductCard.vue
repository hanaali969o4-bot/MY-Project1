<template>
  <div class="product-card">
    <img :src="product.image" class="product-image" :alt="product.name" />
    <div class="product-details">
      <h3 class="product-name">{{ product.name }}</h3>
      <p class="product-description">{{ product.description }}</p>

      <p
        :class="['stock-status', {
          'status-in-stock': product.inStock > 2,
          'status-limited-stock': product.inStock > 0 && product.inStock <= 2,
          'status-out-of-stock': product.inStock === 0,
        }]"
      >
        <span v-if="product.inStock > 2">✅ In Stock</span>
        <span v-else-if="product.inStock > 0">⚠️ Limited Stock</span>
        <span v-else>❌ Out of Stock</span>
      </p>

      <div class="product-footer">
        <p class="product-price">${{ product.price }}</p>
        <button
          @click="$emit('add-to-cart', product)"
          :disabled="product.inStock === 0"
          class="add-to-cart-btn"
        >
          🛒 Add to cart
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  product: {
    type: Object,
    required: true,
  },
});

const emits = defineEmits(['add-to-cart']);
</script>

<style scoped>
.product-card {
  border: 1px solid #e0e0e0;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  height: 100%;
  transition: transform 0.2s ease-in-out;
  background-color: #fff;
}

.product-card:hover {
  transform: translateY(-5px);
}

.product-image {
  width: 100%;
  height: 220px;
  object-fit: cover;
  border-bottom: 1px solid #eee;
}

.product-details {
  padding: 15px;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

.product-name {
  font-size: 1.5em;
  font-weight: bold;
  color: #333;
  margin-bottom: 10px;
}

.product-description {
  font-size: 0.9em;
  color: #666;
  margin-bottom: 15px;
  flex-grow: 1;
}

.stock-status {
  font-weight: bold;
  margin-bottom: 15px;
}

.status-in-stock {
  color: #4CAF50; /* أخضر */
}

.status-limited-stock {
  color: #FFC107; /* أصفر/برتقالي */
}

.status-out-of-stock {
  color: #6c757d; /* رمادي */
}

.product-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: auto;
  padding-top: 15px;
  border-top: 1px solid #eee;
}

.product-price {
  font-size: 1.2em;
  font-weight: bold;
  color: #8E24AA; /* موف فاتح للسعر */
  margin: 0;
}

.add-to-cart-btn {
  background-color: #8E24AA; /* موف فاتح للزرار */
  color: white;
  border: none;
  border-radius: 5px;
  padding: 10px 15px;
  cursor: pointer;
  font-size: 1em;
  transition: background-color 0.3s ease;
}

.add-to-cart-btn:hover:not(:disabled) {
  background-color: #6A1B9A; /* موف أغمق عند التمرير */
}

.add-to-cart-btn:disabled {
  background-color: #ccc;
  cursor: not-allowed;
}
</style>