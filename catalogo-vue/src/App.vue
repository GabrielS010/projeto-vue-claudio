<template>
  <div class="app-container">
    <header>
      <h1>e-Store</h1>
      <div class="cart">
        <span class="cart-counter"> Itens no carrinho: {{ cartCount }}</span>
      </div>
    </header>

    <main>
      <div class="search-bar">
        <input
          type="text"
          v-model="searchQuery"
          placeholder="Pesquisar produto pelo nome..."
        />
      </div>

      <div class="product-grid">
        <ProductCard
          v-for="product in filteredProducts"
          :key="product.id"
          :name="product.name"
          :price="product.price"
          :image="product.image"
          @add-to-cart="handleAddToCart"
        />
      </div>
      
      <div v-if="filteredProducts.length === 0" class="no-results">
        Nenhum produto encontrado na pesquisa.
      </div>
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import ProductCard from './components/ProductCard.vue'

interface Product {
  id: number
  name: string
  price: number
  image: string
}

const cartCount = ref<number>(0)
const searchQuery = ref<string>('')

const products = ref<Product[]>([
  { 
    id: 1, 
    name: 'Teclado Mecânico RGB', 
    price: 350.00, 
    image: 'https://s.zst.com.br/cms-assets/2021/12/teclado-mec-nico-rgb-abertura_easy-resize.com.webp' 
  },
  { 
    id: 2, 
    name: 'Mouse Gamer', 
    price: 200.00, 
    image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQljfEj-VvgusREQ64Fs5_fYxC-ANDkHgokejiYk-Sowg&s=10' 
  },
  { 
    id: 3, 
    name: 'Monitor Ultrawide 29"', 
    price: 1200.00, 
    image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQv-c1tFJfd5jEeMZsXbyrIbIl1nIN60gd3_HfP0pmCtQ&s=10' 
  },
  { 
    id: 4, 
    name: 'Headset Gamer', 
    price: 450.00, 
    image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRepE89Ul-X97xaplPIJCWWoUaKm6VTuB9h7Ubl7SYOug&s=10' 
  },
  { 
    id: 5, 
    name: 'Mousepad Gigante', 
    price: 80.00, 
    image: 'https://cdn.iset.io/assets/55268/produtos/56844/mouse-pad-leao-branco-chines-nuvens-02.jpg' 
  }
])
// Computed property para filtro de busca
const filteredProducts = computed<Product[]>(() => {
  const term = searchQuery.value.toLowerCase()
  return products.value.filter(product =>
    product.name.toLowerCase().includes(term)
  )
})

const handleAddToCart = (): void => {
  cartCount.value++
}
</script>

<style>
:root {
  --bg-color: #0f172a;
  --text-color: #f8fafc;
  --primary-color: #4f46e5;
}

body {
  margin: 0;
  background-color: var(--bg-color);
  color: var(--text-color);
  font-family: system-ui, -apple-system, sans-serif;
}

.app-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-bottom: 20px;
  border-bottom: 1px solid #334155;
  margin-bottom: 20px;
}

header h1 {
  margin: 0;
  font-size: 1.8rem;
}

.cart {
  background-color: var(--primary-color);
  padding: 10px 20px;
  border-radius: 8px;
  font-weight: 600;
}

.search-bar {
  margin-bottom: 30px;
}

.search-bar input {
  width: 100%;
  padding: 15px;
  font-size: 1rem;
  border: 1px solid #334155;
  border-radius: 8px;
  background-color: #1e293b;
  color: var(--text-color);
  box-sizing: border-box;
}

.search-bar input:focus {
  outline: none;
  border-color: var(--primary-color);
}

.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 25px;
}

.no-results {
  text-align: center;
  margin-top: 50px;
  font-size: 1.2rem;
  color: #94a3b8;
}
</style>