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
// Import all menu item images
import friedrice from '../assets/friedrice.jpg'
import beeffriedrice from '../assets/beeffriedrice.jpg'
import grilicfriedrice from '../assets/grilicfriedrice.jpg'
import loklak from '../assets/loklak.jpg'
import noodlevetget from '../assets/noodlevetget.jpg'
import Micha from '../assets/Micha.jpg'
import seafoodnoodle from '../assets/seafoodnoodle.jpg'
import porkrice from '../assets/porkrice.jpg'
import porkribrice from '../assets/porkribrice.jpg'
import phatkaphao from '../assets/phatkaphao.jpg'
import chickenrice from '../assets/chickenrice.jpg'
import beefsteak from '../assets/beefsteak.jpg'
import crispybeef from '../assets/crispybeef.jpg'
import beefsalad from '../assets/beefsalad.jpg'
import beeflab from '../assets/beeflab.jpg'
import beef from '../assets/beef.jpg'
import mimosa from '../assets/mimosa.jpg'
import beefherb from '../assets/beefherb.jpg'
import ppeay from '../assets/ppeay.jpg'
import beefginger from '../assets/beefginger.jpg'
import bokchoy from '../assets/bokchoy.jpg'
import beefstirfrieds from '../assets/beefstirfrieds.jpg'
import frogfried from '../assets/frogfried.jpg'
import friedfrog from '../assets/friedfrog.jpg'
import eelstir from '../assets/eelstir.jpg'
import friedeel from '../assets/friedeel.jpg'
import antongob from '../assets/antongob.png'
import stirchik from '../assets/stirchik.jpg'
import trokunchik from '../assets/trokunchik.jpg'
import bananachik from '../assets/bananachik.jpg'
import chilisaltchik from '../assets/chilisaltchik.jpg'
import garlicchik from '../assets/garlicchik.jpg'
import chiken from '../assets/chiken.jpg'
import chikenngamngov from '../assets/chikenngamngov.jpg'
import porkstir from '../assets/porkstir.jpg'
import trokunpork from '../assets/trokunpork.jpg'
import kroeungbeef from '../assets/kroeungbeef.jpg'
import sweetporkrib from '../assets/sweetporkrib.jpg'
import prokfried from '../assets/prokfried.jpg'
import garlicporkrib from '../assets/garlicporkrib.jpg'
import trokun from '../assets/trokun.jpg'
import vetgetfried from '../assets/vetgetfried.jpg'
import bokchoyvetget from '../assets/bokchoyvetget.jpg'
import brocoli from '../assets/brocoli.jpg'
import chikensoup from '../assets/chikensoup.jpg'
import kuyteav from '../assets/kuyteav.jpg'
import noodlesoup from '../assets/noodlesoup.jpg'
import beefclearsoup from '../assets/beefclearsoup.jpg'
import blackcoffee from '../assets/drink/blackcoffee.png'
import coffeemilk from '../assets/drink/coffeemilk.png'
import greentea from '../assets/drink/greentea.png'
import lemontea from '../assets/drink/lemontea.png'
import coco from '../assets/drink/coco.jpg'
import milktea from '../assets/drink/milktea.png'
import matcha from '../assets/drink/matcha.avif'

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
              image: friedrice
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.1.name'),
              description: this.$t('menu.items.fried_rice_noodle.1.description'),
              price: 1.50,
              image: beeffriedrice
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.2.name'),
              description: this.$t('menu.items.fried_rice_noodle.2.description'),
              price: 1.25,
              image: grilicfriedrice
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.3.name'),
              description: this.$t('menu.items.fried_rice_noodle.3.description'),
              price: 1.75,
              image: loklak
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.4.name'),
              description: this.$t('menu.items.fried_rice_noodle.4.description'),
              price: 1.75,
              image: beeffriedrice
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.5.name'),
              description: this.$t('menu.items.fried_rice_noodle.5.description'),
              price: 1.50,
              image: noodlevetget
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.6.name'),
              description: this.$t('menu.items.fried_rice_noodle.6.description'),
              price: 1.50,
              image: Micha
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.7.name'),
              description: this.$t('menu.items.fried_rice_noodle.7.description'),
              price: 2.00,
              image: seafoodnoodle
            },
            {
              name: this.$t('menu.items.fried_rice_noodle.8.name'),
              description: this.$t('menu.items.fried_rice_noodle.8.description'),
              price: 1.25,
              image: noodlevetget
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
              image: porkrice
            },
            {
              name: this.$t('menu.items.rice.1.name'),
              description: this.$t('menu.items.rice.1.description'),
              price: 1.25,
              image: porkribrice
            },
            {
              name: this.$t('menu.items.rice.2.name'),
              description: this.$t('menu.items.rice.2.description'),
              price: 2.00,
              image: phatkaphao
            },
            {
              name: this.$t('menu.items.rice.3.name'),
              description: this.$t('menu.items.rice.3.description'),
              price: 1.25,
              image: chickenrice
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
              image: beefsteak
            },
            {
              name: this.$t('menu.items.beef_specialities.1.name'),
              description: this.$t('menu.items.beef_specialities.1.description'),
              price: 2.50,
              image: crispybeef
            },
            {
              name: this.$t('menu.items.beef_specialities.2.name'),
              description: this.$t('menu.items.beef_specialities.2.description'),
              price: 2.50,
              image: beefsalad
            },
            {
              name: this.$t('menu.items.beef_specialities.3.name'),
              description: this.$t('menu.items.beef_specialities.3.description'),
              price: 2.50,
              image: beeflab
            },
            {
              name: this.$t('menu.items.beef_specialities.4.name'),
              description: this.$t('menu.items.beef_specialities.4.description'),
              price: 2.50,
              image: beef
            },
            {
              name: this.$t('menu.items.beef_specialities.5.name'),
              description: this.$t('menu.items.beef_specialities.5.description'),
              price: 2.50,
              image: mimosa
            },
            {
              name: this.$t('menu.items.beef_specialities.6.name'),
              description: this.$t('menu.items.beef_specialities.6.description'),
              price: 2.50,
              image: mimosa
            },
            {
              name: this.$t('menu.items.beef_specialities.7.name'),
              description: this.$t('menu.items.beef_specialities.7.description'),
              price: 2.50,
              image: beefherb
            },
            {
              name: this.$t('menu.items.beef_specialities.8.name'),
              description: this.$t('menu.items.beef_specialities.8.description'),
              price: 2.50,
              image: ppeay
            },
            {
              name: this.$t('menu.items.beef_specialities.9.name'),
              description: this.$t('menu.items.beef_specialities.9.description'),
              price: 2.50,
              image: beef
            },
            {
              name: this.$t('menu.items.beef_specialities.10.name'),
              description: this.$t('menu.items.beef_specialities.10.description'),
              price: 2.50,
              image: beefginger
            },
            {
              name: this.$t('menu.items.beef_specialities.11.name'),
              description: this.$t('menu.items.beef_specialities.11.description'),
              price: 2.50,
              image: bokchoy
            },
            {
              name: this.$t('menu.items.beef_specialities.12.name'),
              description: this.$t('menu.items.beef_specialities.12.description'),
              price: 2.50,
              image: beefstirfrieds
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
              image: frogfried
            },
            {
              name: this.$t('menu.items.frog_eel.1.name'),
              description: this.$t('menu.items.frog_eel.1.description'),
              price: 2.50,
              image: frogfried
            },
            {
              name: this.$t('menu.items.frog_eel.2.name'),
              description: this.$t('menu.items.frog_eel.2.description'),
              price: 2.50,
              image: friedfrog
            },
            {
              name: this.$t('menu.items.frog_eel.3.name'),
              description: this.$t('menu.items.frog_eel.3.description'),
              price: 2.50,
              image: friedfrog
            },
            {
              name: this.$t('menu.items.frog_eel.4.name'),
              description: this.$t('menu.items.frog_eel.4.description'),
              price: 2.50,
              image: eelstir
            },
            {
              name: this.$t('menu.items.frog_eel.5.name'),
              description: this.$t('menu.items.frog_eel.5.description'),
              price: 2.509,
              image: friedeel
            },
            {
              name: this.$t('menu.items.frog_eel.6.name'),
              description: this.$t('menu.items.frog_eel.6.description'),
              price: 3.50,
              image: antongob
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
              image: stirchik
            },
            {
              name: this.$t('menu.items.chicken.1.name'),
              description: this.$t('menu.items.chicken.1.description'),
              price: 2.50,
              image: trokunchik
            },
            {
              name: this.$t('menu.items.chicken.2.name'),
              description: this.$t('menu.items.chicken.2.description'),
              price: 2.50,
              image: bananachik
            },
            {
              name: this.$t('menu.items.chicken.3.name'),
              description: this.$t('menu.items.chicken.3.description'),
              price: 2.50,
              image: chilisaltchik
            },
            {
              name: this.$t('menu.items.chicken.4.name'),
              description: this.$t('menu.items.chicken.4.description'),
              price: 2.50,
              image: garlicchik
            },
            {
              name: this.$t('menu.items.chicken.5.name'),
              description: this.$t('menu.items.chicken.5.description'),
              price: 2.50,
              image: chiken
            },
            {
              name: this.$t('menu.items.chicken.6.name'),
              description: this.$t('menu.items.chicken.6.description'),
              price: 2.50,
              image: chikenngamngov
            },
            {
              name: this.$t('menu.items.chicken.7.name'),
              description: this.$t('menu.items.chicken.7.description'),
              price: 2.50,
              image: garlicchik
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
              image: porkstir
            },
            {
              name: this.$t('menu.items.pork.1.name'),
              description: this.$t('menu.items.pork.1.description'),
              price: 2.50,
              image: trokunpork
            },
            {
              name: this.$t('menu.items.pork.2.name'),
              description: this.$t('menu.items.pork.2.description'),
              price: 2.50,
              image: kroeungbeef
            },
            {
              name: this.$t('menu.items.pork.3.name'),
              description: this.$t('menu.items.pork.3.description'),
              price: 2.50,
              image: sweetporkrib
            },
            {
              name: this.$t('menu.items.pork.4.name'),
              description: this.$t('menu.items.pork.4.description'),
              price: 2.50,
              image: prokfried
            },
            {
              name: this.$t('menu.items.pork.5.name'),
              description: this.$t('menu.items.pork.5.description'),
              price: 2.50,
              image: garlicporkrib
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
              image: trokun
            },
            {
              name: this.$t('menu.items.vegetable.1.name'),
              description: this.$t('menu.items.vegetable.1.description'),
              price: 1.25,
              image: vetgetfried
            },
            {
              name: this.$t('menu.items.vegetable.2.name'),
              description: this.$t('menu.items.vegetable.2.description'),
              price: 1.25,
              image: bokchoyvetget
            },
            {
              name: this.$t('menu.items.vegetable.3.name'),
              description: this.$t('menu.items.vegetable.3.description'),
              price: 1.25,
              image: brocoli
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
              image: chikensoup
            },
            {
              name: this.$t('menu.items.soup.1.name'),
              description: this.$t('menu.items.soup.1.description'),
              price: 2.50,
              image: kuyteav
            },
            {
              name: this.$t('menu.items.soup.2.name'),
              description: this.$t('menu.items.soup.2.description'),
              price: 1.25,
              image: noodlesoup
            },
            {
              name: this.$t('menu.items.soup.3.name'),
              description: this.$t('menu.items.soup.3.description'),
              price: 1.25,
              image: beefclearsoup
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
              image: blackcoffee
            },
            {
              name: this.$t('menu.items.drinks.1.name'),
              description: this.$t('menu.items.drinks.1.description'),
              price: 0.63,
              image: coffeemilk
            },
            {
              name: this.$t('menu.items.drinks.2.name'),
              description: this.$t('menu.items.drinks.2.description'),
              price: 0.63,
              image: greentea
            },
            {
              name: this.$t('menu.items.drinks.3.name'),
              description: this.$t('menu.items.drinks.3.description'),
              price: 0.63,
              image: lemontea
            },
            {
              name: this.$t('menu.items.drinks.4.name'),
              description: this.$t('menu.items.drinks.4.description'),
              price: 0.63,
              image: lemontea
            },
            {
              name: this.$t('menu.items.drinks.5.name'),
              description: this.$t('menu.items.drinks.5.description'),
              price: 0.88,
              image: coco
            },
            {
              name: this.$t('menu.items.drinks.6.name'),
              description: this.$t('menu.items.drinks.6.description'),
              price: 0.75,
              image: milktea
            },
            {
              name: this.$t('menu.items.drinks.7.name'),
              description: this.$t('menu.items.drinks.7.description'),
              price: 0.88,
              image: matcha
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