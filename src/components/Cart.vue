<template>
  <!-- Modal Overlay -->
    <div v-if="isOpen" class="modal-overlay" @click="closeCart">
      <div class="modal-content" @click.stop>
        <h2>Your Cart</h2>
        <button @click="closeCart" class="close-btn">&times;</button>

        <div v-if="cart.length === 0" class="empty-cart">
          Your cart is empty.
        </div>

        <div v-else>
          <div v-for="(item, index) in cart" :key="index" class="cart-item">
            <img :src="item.image" :alt="item.name" class="item-image" />
            <div class="item-details">
              <h3>{{ item.name }}</h3>
              <p>Price: ${{ item.price }}</p>
            </div>
            <button @click="removeFromCart(index)" class="remove-btn">Remove</button>
          </div>

          <div class="total">
            <strong>Total: ${{ totalPrice }}</strong>
          </div>

          <button @click="orderNow" class="order-btn">Order Now</button>
        </div>
      </div>
    </div>
</template>

<script setup>
import { inject, computed } from 'vue'

// Props
const props = defineProps({
  modelValue: {
    type: Boolean,
    default: false
  }
})

// Emits
const emit = defineEmits(['update:modelValue'])

// Inject global state
const cart = inject('cart')
const removeFromCart = inject('removeFromCart')

// Computed for v-model
const isOpen = computed({
  get: () => props.modelValue,
  set: (value) => emit('update:modelValue', value)
})

const toggleCart = () => {
  isOpen.value = !isOpen.value
}

const closeCart = () => {
  isOpen.value = false
}

// Computed total price
const totalPrice = computed(() => {
  return cart.value.reduce((sum, item) => sum + item.price, 0)
})

// Order Now function
const orderNow = () => {
  const itemsList = cart.value.map(item => `${item.name} - $${item.price}`).join('\n')
  const message = `Order:\n${itemsList}\nTotal: $${totalPrice.value}`
  const telegramUrl = `https://t.me/chefphat?text=${encodeURIComponent(message)}`
  window.open(telegramUrl, '_blank')
  cart.value = []
}
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-content {
  background: white;
  padding: 20px;
  border-radius: 8px;
  max-width: 500px;
  width: 90%;
  position: relative;
}

.close-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  background: none;
  border: none;
  font-size: 24px;
  cursor: pointer;
}

.empty-cart {
  text-align: center;
  padding: 20px;
}

.cart-item {
  display: flex;
  align-items: center;
  margin-bottom: 15px;
  border-bottom: 1px solid #eee;
  padding-bottom: 10px;
}

.item-image {
  width: 50px;
  height: 50px;
  object-fit: cover;
  margin-right: 15px;
}

.item-details {
  flex: 1;
}

.remove-btn {
  background: #dc3545;
  color: white;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
  border-radius: 3px;
}

.total {
  text-align: right;
  margin: 20px 0;
}

.order-btn {
  background: #28a745;
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 5px;
  width: 100%;
}
</style>