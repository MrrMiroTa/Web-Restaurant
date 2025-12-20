<template>
  <nav>
    <div class="logo">{{ $t('nav.logo') }}</div>
    <ul class="nav-links" :class="{ active: isMenuOpen }" v-show="isMenuOpen || !isMobile">
      <li><router-link to="/" @click="closeMenu">{{ $t('nav.home') }}</router-link></li>
      <li><router-link to="/menu" @click="closeMenu">{{ $t('nav.menu') }}</router-link></li>
      <li><router-link to="/about" @click="closeMenu">{{ $t('nav.about') }}</router-link></li>
      <li><router-link to="/contact" @click="closeMenu">{{ $t('nav.contact') }}</router-link></li>
      <li><button @click="toggleLanguage" class="lang-switch">{{ i18n.locale === 'en' ? 'KM' : 'EN' }}</button></li>
    </ul>
    <button class="hamburger" @click="toggleMenu" v-show="isMobile">
      <span></span>
      <span></span>
      <span></span>
    </button>
  </nav>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import { useI18n } from 'vue-i18n'

const { t, locale: i18nLocale } = useI18n()
const i18n = { locale: i18nLocale }

const isMenuOpen = ref(false)
const isMobile = ref(false)

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