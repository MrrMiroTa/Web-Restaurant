<template>
  <nav>
    <router-link to="/"><div class="logo">{{ $t('nav.logo') }}</div></router-link>
    <ul class="nav-links" :class="{ active: isMenuOpen }" v-show="isMenuOpen || !isMobile">
      <li><router-link to="/" @click="closeMenu">{{ $t('nav.home') }}</router-link></li>
      <li><router-link to="/menu" @click="closeMenu">{{ $t('nav.menu') }}</router-link></li>
      <li><router-link to="/about" @click="closeMenu">{{ $t('nav.about') }}</router-link></li>
      <li><router-link to="/contact" @click="closeMenu">{{ $t('nav.contact') }}</router-link></li>
      <li><button @click="toggleLanguage" class="lang-switch">{{ i18n.locale === 'en' ? 'KM' : 'EN' }}</button></li>
      <li class="cart-icon" @click="toggleCart">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M17,18C15.89,18 15,18.89 15,20A2,2 0 0,0 17,22A2,2 0 0,0 19,20C19,18.89 18.1,18 17,18M1,2V4H3L6.6,11.59L5.24,14.04C5.09,14.32 5,14.65 5,15A2,2 0 0,0 7,17H19V15H7.42A0.25,0.25 0 0,1 7.17,14.75C7.17,14.7 7.18,14.66 7.2,14.63L8.1,13H15.55C16.3,13 16.96,12.58 17.3,11.97L20.88,5.5C20.95,5.34 21,5.17 21,5A1,1 0 0,0 20,4H5.21L4.27,2M7,18C5.89,18 5,18.89 5,20A2,2 0 0,0 7,22A2,2 0 0,0 9,20C9,18.89 8.1,18 7,18Z" fill="white"/>
        </svg>
        <span v-if="cart.length" class="cart-count">{{ cart.length }}</span>
      </li>
    </ul>
    <button class="hamburger" @click="toggleMenu" v-show="isMobile">
      <span></span>
      <span></span>
      <span></span>
    </button>
  </nav>
  <Cart v-model="isCartOpen" />
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount, inject } from 'vue'
import { useI18n } from 'vue-i18n'
import Cart from './Cart.vue'

const { t, locale: i18nLocale } = useI18n()
const i18n = { locale: i18nLocale }

// Inject cart state
const cart = inject('cart')

const isMenuOpen = ref(false)
const isMobile = ref(false)
const isCartOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}

const checkMobile = () => {
  isMobile.value = window.innerWidth <= 768
  if (!isMobile.value) isMenuOpen.value = false
}

const toggleLanguage = () => {
  console.log('Current locale:', i18n.locale.value)
  i18n.locale.value = i18n.locale.value === 'en' ? 'km' : 'en'
  console.log('New locale:', i18n.locale.value)
}

const toggleCart = () => {
  isCartOpen.value = !isCartOpen.value
}

onMounted(() => {
  checkMobile()
  window.addEventListener('resize', checkMobile)
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', checkMobile)
})
</script>

<style scoped>
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: var(--spacing-medium) var(--spacing-large);
  background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
  color: white;
  box-shadow: 0 2px 4px var(--shadow);
  position: sticky;
  top: 0;
  z-index: 1000;
}

.logo {
  font-size: 1.8rem;
  font-weight: bold;
  font-family: var(--font-family-heading);
  color: white;
}

.nav-links {
  list-style: none;
  display: flex;
  gap: var(--spacing-large);
  margin: 0;
  padding: 0;
}

.nav-links li a {
  color: white;
  text-decoration: none;
  font-weight: 500;
  padding: var(--spacing-small) var(--spacing-medium);
  border-radius: var(--border-radius);
  transition: background-color 0.3s ease, color 0.3s ease;
}

.nav-links li a:hover {
  background-color: rgba(255, 255, 255, 0.2);
}

.nav-links li a.router-link-active {
  background-color: var(--accent-color);
  color: var(--primary-color);
  font-weight: 600;
}

.lang-switch {
  background: none;
  border: none;
  color: white;
  font-weight: 500;
  padding: var(--spacing-small) var(--spacing-medium);
  border-radius: var(--border-radius);
  cursor: pointer;
  transition: background-color 0.3s ease, color 0.3s ease;
}

.lang-switch:hover {
  background-color: rgba(255, 255, 255, 0.2);
}

.cart-icon {
  position: relative;
  background: none;
  border: none;
  color: white;
  cursor: pointer;
  padding: var(--spacing-small) var(--spacing-medium);
  border-radius: var(--border-radius);
  transition: background-color 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
}

.cart-icon:hover {
  background-color: rgba(255, 255, 255, 0.2);
}

.cart-count {
  position: absolute;
  top: -8px;
  right: -8px;
  background-color: var(--accent-color);
  color: var(--primary-color);
  border-radius: 50%;
  width: 20px;
  height: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.8rem;
  font-weight: bold;
}

.hamburger {
  display: none;
  flex-direction: column;
  background: none;
  border: none;
  cursor: pointer;
  padding: var(--spacing-small);
}

.hamburger span {
  width: 25px;
  height: 3px;
  background: white;
  margin: 3px 0;
  transition: 0.3s;
  border-radius: 2px;
}

.hamburger:hover span {
  background: var(--accent-color);
}

@media (max-width: 768px) {
  nav {
    padding: var(--spacing-medium);
  }

  .logo {
    font-size: 1.5rem;
  }

  .nav-links {
    position: absolute;
    top: 100%;
    left: 0;
    width: 100%;
    background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
    flex-direction: column;
    padding: var(--spacing-large);
    box-shadow: 0 4px 8px var(--shadow);
    display: none;
  }

  .nav-links.active {
    display: flex;
  }

  .nav-links li {
    margin: var(--spacing-small) 0;
  }

  .nav-links li a {
    display: block;
    padding: var(--spacing-medium);
    text-align: center;
  }

  .hamburger {
    display: flex;
  }
}
</style>