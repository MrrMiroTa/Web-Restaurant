<template>
  <div class="home">
    <!-- Hero Section -->
    <section class="hero">
     <h1>{{ $t('home.hero.title') }}</h1>
      <p>{{ $t('home.hero.subtitle') }}</p>
      <router-link to="/menu" class="btn">{{ $t('home.hero.view_menu') }}</router-link>
    </section>

    <!-- Featured Dishes Section -->
    <section class="featured-dishes">
      <h2>{{ $t('home.best_seller') }}</h2>
      <div class="dishes-grid">
        <div class="dish" v-for="dish in dishes" :key="dish.id">
          <img :src="dish.image" :alt="dish.name">
          <h3>{{ dish.name }}</h3>
          <p>{{ dish.description }}</p>
        </div>
      </div>
    </section>

    <!-- Testimonials Section -->
    <section class="testimonials">
      <h2>{{ $t('home.testimonials.title') }}</h2>
      <div class="testimonial" v-for="testimonial in testimonials" :key="testimonial.id">
        <p>"{{ testimonial.quote }}"</p>
        <cite>- {{ testimonial.name }}</cite>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Home',
  computed: {
    dishes() {
      return [
        { id: 1, name: this.$t('home.dishes.0.name'), description: this.$t('home.dishes.0.description'), image: '/assets/antongob.png' },
        { id: 2, name: this.$t('home.dishes.1.name'), description: this.$t('home.dishes.1.description'), image: '/assets/kuyteav.jpg' },
        { id: 3, name: this.$t('home.dishes.2.name'), description: this.$t('home.dishes.2.description'), image: '/assets/beefherb.jpg' },
        { id: 4, name: this.$t('home.dishes.3.name'), description: this.$t('home.dishes.3.description'), image: '/assets/beeflab.jpg' }
      ]
    },
    testimonials() {
      return [
        { id: 1, quote: this.$t('home.testimonials.items.0.quote'), name: this.$t('home.testimonials.items.0.name') },
        { id: 2, quote: this.$t('home.testimonials.items.1.quote'), name: this.$t('home.testimonials.items.1.name') },
        { id: 3, quote: this.$t('home.testimonials.items.2.quote'), name: this.$t('home.testimonials.items.2.name') }
      ]
    }
  }
}
</script>

<style scoped>
.home {
  justify-content: center;
  /* Basic container styles */
}

.hero {
  background: url('/assets/bg.png') no-repeat center center / cover;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  color: white;
  text-align: center;
  padding: 0 var(--spacing-large);
}

.hero h1 {
  font-size: 4rem;
  margin-bottom: var(--spacing-medium);
  text-shadow: 2px 2px 4px var(--shadow);
}

.hero p {
  font-size: 1.5rem;
  margin-bottom: var(--spacing-large);
}

.btn {
  background: var(--accent-color);
  color: var(--primary-color);
  padding: var(--spacing-medium) var(--spacing-large);
  text-decoration: none;
  border-radius: var(--border-radius);
  font-weight: 600;
  transition: all 0.3s ease;
  box-shadow: 0 4px 8px var(--shadow);
}

.btn:hover {
  background: white;
  transform: translateY(-2px);
  box-shadow: 0 6px 12px var(--shadow);
}

.featured-dishes {
  padding: var(--spacing-large) 0;
  text-align: center;
  background: var(--accent-color);
}

.featured-dishes h2 {
  color: var(--secondary-color);
  margin-bottom: var(--spacing-large);
}

.dishes-grid {
  display: grid;
  grid-template-columns: 1fr; /* Mobile: 1 column */
  gap: var(--spacing-large);
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--spacing-medium);
}

.dish {
  background: white;
  border-radius: var(--border-radius);
  box-shadow: 0 4px 8px var(--shadow);
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.dish:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 16px var(--shadow);
}

.dish img {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.dish h3 {
  padding: var(--spacing-medium);
  color: var(--text-color);
  font-size: 1.25rem;
}

.dish p {
  padding: 0 var(--spacing-medium) var(--spacing-medium);
  color: #666;
}

.testimonials {
  padding: var(--spacing-large) 0;
  background: var(--background-color);
  text-align: center;
}

.testimonials h2 {
  color: var(--secondary-color);
  margin-bottom: var(--spacing-large);
}

.testimonial {
  background: var(--accent-color);
  border-radius: var(--border-radius);
  padding: var(--spacing-large);
  margin: var(--spacing-medium) auto;
  max-width: 600px;
  box-shadow: 0 4px 8px var(--shadow);
  transition: transform 0.3s ease;
}

.testimonial:hover {
  transform: translateY(-2px);
}

.testimonial p {
  font-style: italic;
  margin-bottom: var(--spacing-small);
}

.testimonial cite {
  font-weight: 600;
  color: var(--primary-color);
}

/* Responsive Design - Mobile First */
@media (min-width: 768px) {
  .hero {
    padding: 0 var(--spacing-large);
  }

  .hero h1 {
    font-size: 3rem;
  }

  .hero p {
    font-size: 1.4rem;
  }

  .dishes-grid {
    grid-template-columns: repeat(2, 1fr); /* Tablet: 2 columns */
    padding: 0 var(--spacing-large);
  }

  .testimonial {
    margin: var(--spacing-medium) auto;
  }
}

@media (min-width: 1024px) {
  .hero h1 {
    font-size: 4rem;
  }

  .hero p {
    font-size: 1.5rem;
  }

  .dishes-grid {
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); /* Desktop: 3-4 columns */
  }
}
</style>