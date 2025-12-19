<template>
  <div class="menu">
    <div class="tabs">
      <button
        v-for="category in categories"
        :key="category.key"
        @click="activeCategory = category.key"
        :class="{ active: activeCategory === category.key }"
        class="tab-button"
      >
        {{ category.name }}
      </button>
    </div>
    <div class="items-grid">
      <div
        v-for="item in getActiveItems()"
        :key="item.name"
        class="item-card"
      >
        <img :src="item.image" :alt="item.name" class="item-image" />
        <h3 class="item-name">{{ item.name }}</h3>
        <p class="item-description">{{ item.description }}</p>
        <p class="item-price">${{ item.price }}</p>
        <button class="add-to-cart-btn">{{ $t('menu.add_to_cart') }}</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Menu',
  data() {
    return {
      activeCategory: 'fried_rice_noodle'
    };
  },
  computed: {
    categories() {
      return [
        {
          name: this.$t('menu.categories.fried_rice_noodle'),
          key: 'fried_rice_noodle',
          items: [
            {
              name: this.$t('menu.items.fried_rice_noodle.0.name'),
              description: this.$t('menu.items.fried_rice_noodle.0.description'),
              price: 2.00,
              image: '/src/assets/friedrice.jpg'
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.1.name'),
              description: this.$t('menu.items.fried_rice_noodle.1.description'),
              price: 1.50,
              image: '/src/assets/beeffriedrice.jpg'
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.2.name'),
              description: this.$t('menu.items.fried_rice_noodle.2.description'),
              price: 1.25,
              image: '/src/assets/grilicfriedrice.jpg'
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.3.name'),
              description: this.$t('menu.items.fried_rice_noodle.3.description'),
              price: 1.75,
              image: '/src/assets/loklak.jpg'
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.4.name'),
              description: this.$t('menu.items.fried_rice_noodle.4.description'),
              price: 1.75,
              image: '/src/assets/beeffriedrice.jpg'
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.5.name'),
              description: this.$t('menu.items.fried_rice_noodle.5.description'),
              price: 1.50,
              image: '/src/assets/noodlevetget.jpg'
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.6.name'),
              description: this.$t('menu.items.fried_rice_noodle.6.description'),
              price: 1.50,
              image: '/src/assets/micha.jpg'
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.7.name'),
              description: this.$t('menu.items.fried_rice_noodle.7.description'),
              price: 2.00,
              image: '/src/assets/seafoodnoodle.jpg'
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.8.name'),
              description: this.$t('menu.items.fried_rice_noodle.8.description'),
              price: 1.25,
              image: '/src/assets/noodlevetget.jpg'
            }
          ]
        },
        {
          name: this.$t('menu.categories.rice'),
          key: 'rice',
          items: [
            {
              name: this.$t('menu.items.rice.0.name'),
              description: this.$t('menu.items.rice.0.description'),
              price: 1.25,
              image: '/src/assets/porkrice.jpg'
            },
            {
              name: this.$t('menu.items.rice.1.name'),
              description: this.$t('menu.items.rice.1.description'),
              price: 1.25,
              image: '/src/assets/porkribrice.jpg'
            },
            {
              name: this.$t('menu.items.rice.2.name'),
              description: this.$t('menu.items.rice.2.description'),
              price: 2.00,
              image: '/src/assets/phatkaphao.jpg'
            },
            {
              name: this.$t('menu.items.rice.3.name'),
              description: this.$t('menu.items.rice.3.description'),
              price: 1.25,
              image: '/src/assets/chickenrice.jpg'
            }
          ]
        },
        {
          name: this.$t('menu.categories.beef_specialities'),
          key: 'beef_specialities',
          items: [
            {
              name: this.$t('menu.items.beef_specialities.0.name'),
              description: this.$t('menu.items.beef_specialities.0.description'),
              price: 3.75,
              image: '/src/assets/beefsteak.jpg'
            },
            {
              name: this.$t('menu.items.beef_specialities.1.name'),
              description: this.$t('menu.items.beef_specialities.1.description'),
              price: 2.50,
              image: '/src/assets/crispybeef.jpg'
            },
            {
              name: this.$t('menu.items.beef_specialities.2.name'),
              description: this.$t('menu.items.beef_specialities.2.description'),
              price: 2.50,
              image: '/src/assets/beefsalad.jpg'
            },
            {
              name: this.$t('menu.items.beef_specialities.3.name'),
              description: this.$t('menu.items.beef_specialities.3.description'),
              price: 2.50,
              image: '/src/assets/beeflab.jpg'
            },
            {
              name: this.$t('menu.items.beef_specialities.4.name'),
              description: this.$t('menu.items.beef_specialities.4.description'),
              price: 2.50,
              image: '/src/assets/beef.jpg'
            },
            {
              name: this.$t('menu.items.beef_specialities.5.name'),
              description: this.$t('menu.items.beef_specialities.5.description'),
              price: 2.50,
              image: '/src/assets/mimosa.jpg'
            },
            {
              name: this.$t('menu.items.beef_specialities.6.name'),
              description: this.$t('menu.items.beef_specialities.6.description'),
              price: 2.50,
              image: '/src/assets/mimosa.jpg'
            },
            {
              name: this.$t('menu.items.beef_specialities.7.name'),
              description: this.$t('menu.items.beef_specialities.7.description'),
              price: 2.50,
              image: '/src/assets/beefherb.jpg'
            },
            {
              name: this.$t('menu.items.beef_specialities.8.name'),
              description: this.$t('menu.items.beef_specialities.8.description'),
              price: 2.50,
              image: '/src/assets/ppeay.jpg'
            },
            {
              name: this.$t('menu.items.beef_specialities.9.name'),
              description: this.$t('menu.items.beef_specialities.9.description'),
              price: 2.50,
              image: '/src/assets/beef.jpg'
            },
            {
              name: this.$t('menu.items.beef_specialities.10.name'),
              description: this.$t('menu.items.beef_specialities.10.description'),
              price: 2.50,
              image: '/src/assets/beefginger.jpg'
            },
            {
              name: this.$t('menu.items.beef_specialities.11.name'),
              description: this.$t('menu.items.beef_specialities.11.description'),
              price: 2.50,
              image: '/src/assets/bokchoy.jpg'
            },
            {
              name: this.$t('menu.items.beef_specialities.12.name'),
              description: this.$t('menu.items.beef_specialities.12.description'),
              price: 2.50,
              image: '/src/assets/beefstirfrieds.jpg'
            }
          ]
        },
        {
          name: this.$t('menu.categories.frog_eel'),
          key: 'frog_eel',
          items: [
            {
              name: this.$t('menu.items.frog_eel.0.name'),
              description: this.$t('menu.items.frog_eel.0.description'),
              price: 2.50,
              image: '/src/assets/frogfried.jpg'
            },
            {
              name: this.$t('menu.items.frog_eel.1.name'),
              description: this.$t('menu.items.frog_eel.1.description'),
              price: 2.50,
              image: '/src/assets/frogfried.jpg'
            },
            {
              name: this.$t('menu.items.frog_eel.2.name'),
              description: this.$t('menu.items.frog_eel.2.description'),
              price: 2.50,
              image: '/src/assets/friedfrog.jpg'
            },
            {
              name: this.$t('menu.items.frog_eel.3.name'),
              description: this.$t('menu.items.frog_eel.3.description'),
              price: 2.50,
              image: '/src/assets/friedfrog.jpg'
            },
            {
              name: this.$t('menu.items.frog_eel.4.name'),
              description: this.$t('menu.items.frog_eel.4.description'),
              price: 2.50,
              image: '/src/assets/eelstir.jpg'
            },
            {
              name: this.$t('menu.items.frog_eel.5.name'),
              description: this.$t('menu.items.frog_eel.5.description'),
              price: 2.509,
              image: '/src/assets/friedeel.jpg'
            },
            {
              name: this.$t('menu.items.frog_eel.6.name'),
              description: this.$t('menu.items.frog_eel.6.description'),
              price: 3.50,
              image: '/src/assets/antongob.png'
            }
          ]
        },
        {
          name: this.$t('menu.categories.chicken'),
          key: 'chicken',
          items: [
            {
              name: this.$t('menu.items.chicken.0.name'),
              description: this.$t('menu.items.chicken.0.description'),
              price: 2.50,
              image: '/src/assets/stirchik.jpg'
            },
            {
              name: this.$t('menu.items.chicken.1.name'),
              description: this.$t('menu.items.chicken.1.description'),
              price: 2.50,
              image: '/src/assets/trokunchik.jpg'
            },
            {
              name: this.$t('menu.items.chicken.2.name'),
              description: this.$t('menu.items.chicken.2.description'),
              price: 2.50,
              image: '/src/assets/bananachik.jpg'
            },
            {
              name: this.$t('menu.items.chicken.3.name'),
              description: this.$t('menu.items.chicken.3.description'),
              price: 2.50,
              image: '/src/assets/chilisaltchik.jpg'
            },
            {
              name: this.$t('menu.items.chicken.4.name'),
              description: this.$t('menu.items.chicken.4.description'),
              price: 2.50,
              image: '/src/assets/garlicchik.jpg'
            },
            {
              name: this.$t('menu.items.chicken.5.name'),
              description: this.$t('menu.items.chicken.5.description'),
              price: 2.50,
              image: '/src/assets/chiken.jpg'
            },
            {
              name: this.$t('menu.items.chicken.6.name'),
              description: this.$t('menu.items.chicken.6.description'),
              price: 2.50,
              image: '/src/assets/chikenngamngov.jpg'
            },
            {
              name: this.$t('menu.items.chicken.7.name'),
              description: this.$t('menu.items.chicken.7.description'),
              price: 2.50,
              image: '/src/assets/garlicchik.jpg'
            }
          ]
        },
        {
          name: this.$t('menu.categories.pork'),
          key: 'pork',
          items: [
            {
              name: this.$t('menu.items.pork.0.name'),
              description: this.$t('menu.items.pork.0.description'),
              price: 2.50,
              image: '/src/assets/porkstir.jpg'
            },
            {
              name: this.$t('menu.items.pork.1.name'),
              description: this.$t('menu.items.pork.1.description'),
              price: 2.50,
              image: '/src/assets/trokunpork.jpg'
            },
            {
              name: this.$t('menu.items.pork.2.name'),
              description: this.$t('menu.items.pork.2.description'),
              price: 2.50,
              image: '/src/assets/kroeungbeef.jpg'
            },
            {
              name: this.$t('menu.items.pork.3.name'),
              description: this.$t('menu.items.pork.3.description'),
              price: 2.50,
              image: '/src/assets/sweetporkrib.jpg'
            },
            {
              name: this.$t('menu.items.pork.4.name'),
              description: this.$t('menu.items.pork.4.description'),
              price: 2.50,
              image: '/src/assets/prokfried.jpg'
            },
            {
              name: this.$t('menu.items.pork.5.name'),
              description: this.$t('menu.items.pork.5.description'),
              price: 2.50,
              image: '/src/assets/garlicporkrib.jpg'
            }
          ]
        },
        {
          name: this.$t('menu.categories.vegetable'),
          key: 'vegetable',
          items: [
            {
              name: this.$t('menu.items.vegetable.0.name'),
              description: this.$t('menu.items.vegetable.0.description'),
              price: 1.25,
              image: '/src/assets/trokun.jpg'
            },
            {
              name: this.$t('menu.items.vegetable.1.name'),
              description: this.$t('menu.items.vegetable.1.description'),
              price: 1.25,
              image: '/src/assets/vetgetfried.jpg'
            },
            {
              name: this.$t('menu.items.vegetable.2.name'),
              description: this.$t('menu.items.vegetable.2.description'),
              price: 1.25,
              image: '/src/assets/bokchoyvetget.jpg'
            },
            {
              name: this.$t('menu.items.vegetable.3.name'),
              description: this.$t('menu.items.vegetable.3.description'),
              price: 1.25,
              image: '/src/assets/brocoli.jpg'
            }
          ]
        },
        {
          name: this.$t('menu.categories.soup'),
          key: 'soup',
          items: [
            {
              name: this.$t('menu.items.soup.0.name'),
              description: this.$t('menu.items.soup.0.description'),
              price: 2.50,
              image: '/src/assets/chikensoup.jpg'
            },
            {
              name: this.$t('menu.items.soup.1.name'),
              description: this.$t('menu.items.soup.1.description'),
              price: 2.50,
              image: '/src/assets/kuyteav.jpg'
            },
            {
              name: this.$t('menu.items.soup.2.name'),
              description: this.$t('menu.items.soup.2.description'),
              price: 1.25,
              image: '/src/assets/noodlesoup.jpg'
            },
            {
              name: this.$t('menu.items.soup.3.name'),
              description: this.$t('menu.items.soup.3.description'),
              price: 1.25,
              image: '/src/assets/beefclearsoup.jpg'
            }
          ]
        },
        {
          name: this.$t('menu.categories.drinks'),
          key: 'drinks',
          items: [
            {
              name: this.$t('menu.items.drinks.0.name'),
              description: this.$t('menu.items.drinks.0.description'),
              price: 0.63,
              image: '/src/assets/drink/blackcoffee.png'
            },
            {
              name: this.$t('menu.items.drinks.1.name'),
              description: this.$t('menu.items.drinks.1.description'),
              price: 0.63,
              image: '/src/assets/drink/coffeemilk.png'
            },
            {
              name: this.$t('menu.items.drinks.2.name'),
              description: this.$t('menu.items.drinks.2.description'),
              price: 0.63,
              image: '/src/assets/drink/greentea.png'
            },
            {
              name: this.$t('menu.items.drinks.3.name'),
              description: this.$t('menu.items.drinks.3.description'),
              price: 0.63,
              image: '/src/assets/drink/lemontea.png'
            },
            {
              name: this.$t('menu.items.drinks.4.name'),
              description: this.$t('menu.items.drinks.4.description'),
              price: 0.63,
              image: '/src/assets/drink/lemontea.png'
            },
            {
              name: this.$t('menu.items.drinks.5.name'),
              description: this.$t('menu.items.drinks.5.description'),
              price: 0.88,
              image: '/src/assets/drink/coco.jpg'
            },
            {
              name: this.$t('menu.items.drinks.6.name'),
              description: this.$t('menu.items.drinks.6.description'),
              price: 0.75,
              image: '/src/assets/drink/milktea.png'
            },
            {
              name: this.$t('menu.items.drinks.7.name'),
              description: this.$t('menu.items.drinks.7.description'),
              price: 0.88,
              image: '/src/assets/drink/matcha.avif'
            }
          ]
        }
      ]
    }
  },
  methods: {
    getActiveItems() {
      const category = this.categories.find(cat => cat.key === this.activeCategory);
      return category ? category.items : [];
    }
  }
};
</script>

<style scoped>
.menu {
  padding: var(--spacing-large) 0;
  max-width: 1200px;
  margin: 0 auto;
}

.tabs {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  margin-bottom: var(--spacing-large);
  gap: var(--spacing-small);
}

.tab-button {
  padding: var(--spacing-medium) var(--spacing-large);
  border: 2px solid var(--primary-color);
  background-color: white;
  color: var(--primary-color);
  cursor: pointer;
  border-radius: var(--border-radius);
  font-weight: 500;
  transition: all 0.3s ease;
}

.tab-button:hover {
  background-color: var(--primary-color);
  color: white;
}

.tab-button.active {
  background-color: var(--primary-color);
  color: white;
  box-shadow: 0 4px 8px var(--shadow);
}

.items-grid {
  display: grid;
  grid-template-columns: 1fr; /* Mobile: 1 column */
  gap: var(--spacing-large);
  padding: 0 var(--spacing-medium);
}

.item-card {
  background: white;
  border-radius: var(--border-radius);
  padding: var(--spacing-large);
  text-align: center;
  box-shadow: 0 4px 8px var(--shadow);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  overflow: hidden;
}

.item-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 16px var(--shadow);
}

.item-image {
  width: 100%;
  height: 180px;
  object-fit: cover;
  border-radius: var(--border-radius);
  margin-bottom: var(--spacing-medium);
}

.item-name {
  margin: 0 0 var(--spacing-small) 0;
  font-size: 1.25rem;
  color: var(--text-color);
}

.item-description {
  color: #666;
  margin: 0 0 var(--spacing-medium) 0;
  font-size: 0.9rem;
}

.item-price {
  font-weight: 600;
  margin: 0 0 var(--spacing-medium) 0;
  color: var(--secondary-color);
  font-size: 1.1rem;
}

.add-to-cart-btn {
  background-color: var(--primary-color);
  color: white;
  border: none;
  padding: var(--spacing-medium) var(--spacing-large);
  border-radius: var(--border-radius);
  cursor: pointer;
  font-weight: 600;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.add-to-cart-btn:hover {
  background-color: var(--secondary-color);
  transform: translateY(-2px);
}

/* Responsive Design - Mobile First */
@media (min-width: 768px) {
  .tabs {
    flex-direction: row;
    justify-content: center;
  }

  .tab-button {
    width: auto;
  }

  .items-grid {
    grid-template-columns: repeat(2, 1fr); /* Tablet: 2 columns */
    padding: 0 var(--spacing-large);
  }

  .item-card {
    padding: var(--spacing-large);
  }
}

@media (min-width: 1024px) {
  .items-grid {
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); /* Desktop: 3-4 columns */
  }
}
</style>