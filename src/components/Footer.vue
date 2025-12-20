<template>
  <footer>
    <div class="footer-content">
      <div class="links">
        <router-link to="/">{{ $t('footer.home') }}</router-link>
        <router-link to="/menu">{{ $t('footer.menu') }}</router-link>
        <router-link to="/about">{{ $t('footer.about') }}</router-link>
        <router-link to="/contact">{{ $t('footer.contact') }}</router-link>
      </div>
      <div class="social">
        <a href="https://www.facebook.com/share/1C7uknxT1J/" target="_blank" rel="noopener noreferrer"><span>{{ $t('footer.facebook') }}</span></a>
        <a href="https://t.me/chefphat" target="_blank" rel="noopener noreferrer"><span>{{ $t('footer.telegram') }}</span></a>
      </div>
      <p>&copy 2025 Friends Meet's | Powered By <a href="https://t.me/DoeunSoPhors" target="_blank" rel="noopener noreferrer" style="color: white ;">Mrr. Phors</a></p>
    </div>
  </footer>
</template>

<script>
export default {
  // No script needed
}
</script>

<style scoped>
footer {
  background: linear-gradient(90deg, var(--secondary-color), var(--primary-color));
  color: white;
  padding: var(--spacing-large) 0;
  text-align: center;
  margin-top: auto;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--spacing-large);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--spacing-large);
}

.links {
  display: flex;
  gap: var(--spacing-large);
  flex-wrap: wrap;
  justify-content: center;
}

.links a {
  color: white;
  text-decoration: none;
  font-weight: 500;
  padding: var(--spacing-small) var(--spacing-medium);
  border-radius: var(--border-radius);
  transition: background-color 0.3s ease, color 0.3s ease;
}

.links a:hover {
  background-color: var(--accent-color);
  color: var(--primary-color);
}

.social {
  display: flex;
  gap: var(--spacing-large);
  flex-wrap: wrap;
  justify-content: center;
}

.social a span {
  background: rgba(255, 255, 255, 0.1);
  padding: var(--spacing-small) var(--spacing-medium);
  border-radius: var(--border-radius);
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.social a span:hover {
  background: var(--accent-color);
  color: var(--primary-color);
}

.footer-content p {
  margin: 0;
  font-size: 0.9rem;
  opacity: 0.8;
}

@media (max-width: 768px) {
  .footer-content {
    padding: 0 var(--spacing-medium);
  }

  .links {
    flex-direction: column;
    gap: var(--spacing-medium);
  }

  .social {
    flex-direction: column;
    gap: var(--spacing-medium);
  }
}
</style>