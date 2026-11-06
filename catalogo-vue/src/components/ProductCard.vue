<template>
  <div class="product-card">
    <img :src="image" :alt="name" class="product-image" />
    <div class="product-info">
      <h3 class="product-name">{{ name }}</h3>
      <p class="product-price">{{ formattedPrice }}</p>
      <button @click="addToCart" class="add-btn">Adicionar ao Carrinho</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'

// Definição das Props com TypeScript
interface Props {
  name: string
  price: number
  image: string
}

const props = defineProps<Props>()

// Definição do Evento de Emissão tipado
const emit = defineEmits<{
  (e: 'add-to-cart'): void
}>()

// Formatação amigável do preço
const formattedPrice = computed<string>(() => {
  return props.price.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' })
})

const addToCart = (): void => {
  emit('add-to-cart')
}
</script>

<style scoped>
.product-card {
  background-color: #1e293b;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.4);
  transition: transform 0.2s ease;
  display: flex;
  flex-direction: column;
}

.product-card:hover {
  transform: translateY(-5px);
}

.product-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.product-info {
  padding: 15px;
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.product-name {
  margin: 0 0 10px 0;
  font-size: 1.1rem;
}

.product-price {
  margin: 0 0 20px 0;
  font-size: 1.3rem;
  font-weight: bold;
  color: #818cf8;
  flex-grow: 1;
}

.add-btn {
  background-color: #4f46e5;
  color: #fff;
  border: none;
  padding: 12px;
  border-radius: 6px;
  cursor: pointer;
  font-weight: 600;
  transition: background-color 0.2s;
}

.add-btn:hover {
  background-color: #4338ca;
}
</style>