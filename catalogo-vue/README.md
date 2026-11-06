# Catálogo de Produtos Vue.js 3 + TypeScript

## Objetivo do Projeto
Atividade prática da disciplina de Programação Web I (Engenharia de Software). O objetivo é aplicar os conceitos fundamentais do framework Vue.js 3 utilizando TypeScript, focando em reatividade, vinculação de dados (data binding) e componentização de interfaces, desenvolvendo um catálogo interativo com carrinho de compras.

## Tecnologias Utilizadas
- Vue.js 3 (Composition API com `<script setup lang="ts">`)
- TypeScript
- Vite
- HTML5, CSS3

## Funcionalidades Implementadas
- **Componentização & Tipagem:** Componente `ProductCard` com interfaces TypeScript para validação estática das `props`.
- **Reatividade e Eventos:** O componente filho emite o evento `@add-to-cart` capturado pelo `App.vue` para atualizar o contador global de itens no carrinho em tempo real, sem recarregar a página.
- **Busca em Tempo Real:** Campo de pesquisa integrado usando a diretiva `v-model` em conjunto com uma propriedade `computed` tipada para refiltrar os produtos instantaneamente.
- **UI/UX e Responsividade:** Layout moderno com tema escuro, cartões organizados com imagens reais dos produtos e CSS Grid responsivo.

## Como Executar a Aplicação Localmente

1. Abra o terminal na pasta raiz do projeto (`catalogo-vue`).
2. Instale as dependências:
   ```bash
   npm install