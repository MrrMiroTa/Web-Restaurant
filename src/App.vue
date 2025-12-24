<script setup>
import { ref, provide } from 'vue'
import NavBar from './components/NavBar.vue'
import Footer from './components/Footer.vue'
import { Analytics } from "@vercel/analytics/next"

// Reactive cart state
const cart = ref([])

// Function to add item to cart
const addToCart = (item) => {
  cart.value.push(item)
}

// Function to remove item from cart
const removeFromCart = (index) => {
  cart.value.splice(index, 1)
}

// Function to clear cart
const clearCart = () => {
  cart.value = []
}

// Provide cart state and functions to child components
provide('cart', cart)
provide('addToCart', addToCart)
provide('removeFromCart', removeFromCart)
provide('clearCart', clearCart)
</script>

<template>
  <NavBar />
  <router-view />
  <Analytics />
  <Footer />
</template>