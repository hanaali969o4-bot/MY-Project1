<template>
  <div>
    <Navbar :cartCount="cartCount" />

    <div class="container my-5">
      <h2 class="section-title">🛍 Our Products</h2>
      <p v-if="products.length === 0" class="no-products-message">No products available</p>
      <div v-show="products.length > 0" class="products-grid">
        <div
          v-for="product in products"
          :key="product.id"
          class="product-grid-item"
        >
          <ProductCard :product="product" @add-to-cart="addToCart" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import Navbar from './components/Navbar.vue';
import ProductCard from './components/ProductCard.vue';

// روابط الصور الجديدة
const cameraImage = 'https://aitnews.com/wp-content/uploads/2020/02/hero-xl.jpg';
const tShirtsImage = 'https://i.ytimg.com/vi/o_mvQ1K8MP8/maxresdefault.jpg';
const ringImage = 'https://www.3roos.com/wp-content/uploads/2019/04/4-32.jpg';
const laptopImage = 'https://img.youm7.com/large/4201619414506391.jpg';
const mobileImage = 'https://tse2.mm.bing.net/th/id/OIP.3iF61O2HF2JYjFxu-OsO2AHaHa?rs=1&pid=ImgDetMain&o=7&rm=3';
const watchesImage = 'https://i.ytimg.com/vi/226ppNjbBjI/maxresdefault.jpg';
const mensWatchImage = 'https://www.mikzon.com/u_file/1907/photo/617b9774ac.jpg'; // رابط صورة ساعة رجالي
const perfumeImage = 'https://joumla-eg.b-cdn.net/wp-content/uploads/2023/05/Screenshot_20230507_175516.jpg'; // رابط صورة عطر
const headphonesImage = 'https://tse3.mm.bing.net/th/id/OIP.7R5wOQj-W5EZ5ObSDE8JtAHaHa?w=600&h=600&rs=1&pid=ImgDetMain&o=7&rm=3'; // رابط صورة سماعات


const products = ref([
  {
    id: 1,
    name: 'Vintage Camera',
    price: 350,
    inStock: 5,
    description: 'A classic film camera for nostalgic photography.',
    image: cameraImage,
  },
  {
    id: 2,
    name: 'T-Shirts Set',
    price: 45,
    inStock: 15,
    description: 'A collection of stylish t-shirts for girls.',
    image: tShirtsImage,
  },
  {
    id: 3,
    name: 'Diamond Ring',
    price: 500,
    inStock: 8,
    description: 'An elegant silver ring with a sparkling diamond.',
    image: ringImage,
  },
  {
    id: 4,
    name: 'Laptop',
    price: 1200,
    inStock: 4,
    description: 'Powerful and portable laptop for all your needs.',
    image: laptopImage,
  },
  {
    id: 5,
    name: 'Smartphone',
    price: 900,
    inStock: 3,
    description: 'A modern smartphone with a stunning display and camera.',
    image: mobileImage,
  },
  {
    id: 6,
    name: 'Elegant Watches',
    price: 180,
    inStock: 10,
    description: 'A collection of elegant watches for men and women.',
    image: watchesImage,
  },
  {
    id: 7,
    name: 'Men\'s Wristwatch', // اسم المنتج الجديد
    price: 250, // سعر
    inStock: 6, // كمية
    description: 'A luxurious wristwatch designed for modern men.', // وصف
    image: mensWatchImage,
  },
  {
    id: 8,
    name: 'Luxury Perfume', // اسم المنتج الجديد
    price: 100, // سعر
    inStock: 12, // كمية
    description: 'A captivating fragrance that leaves a lasting impression.', // وصف
    image: perfumeImage,
  },
  {
    id: 9,
    name: 'Wireless Headphones', // اسم المنتج الجديد
    price: 70, // سعر
    inStock: 20, // كمية
    description: 'High-quality wireless headphones for immersive audio.', // وصف
    image: headphonesImage,
  },
]);

const cart = ref([]);
const cartCount = computed(() => cart.value.length);

const addToCart = (product) => {
  cart.value.push(product);
  alert(`${product.name} has been added to the cart!`);
};
</script>

<style scoped>
/* نفس الـ CSS السابق لـ App.vue */
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

.section-title {
  text-align: center;
  font-size: 2.5em;
  color: #6A1B9A;
  margin-bottom: 40px;
  font-weight: bold;
}

.no-products-message {
  text-align: center;
  color: #888;
  font-size: 1.2em;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 25px;
  padding: 20px;
}

.product-grid-item {
  display: flex;
  justify-content: center;
}
</style>