<template>
  <div class="about">
    <!-- Hero Image Section -->
    <section class="hero" :style="{ background: `linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)), url(${heroImage}) no-repeat center center`, backgroundSize: 'cover' }">
      <div class="hero-content">
        <h1>{{ $t('about.hero.title') }}</h1>
        <p>{{ $t('about.hero.subtitle') }}</p>
      </div>
    </section>

    <!-- Restaurant Story Section -->
    <section class="story">
      <div class="container">
        <h2>{{ $t('about.story.title') }}</h2>
        <p>{{ $t('about.story.p1') }}</p>
        <p>{{ $t('about.story.p2') }}</p>
      </div>
    </section>

    <!-- Team Section -->
    <section class="team">
      <div class="container">
        <h2>{{ $t('about.team.title') }}</h2>
        <div class="team-members">
          <div class="member" v-for="(member, index) in teamMembers" :key="index">
            <div class="member-photo" :style="{ backgroundImage: `url(${member.photo})` }"></div>
            <h3>{{ member.name }}</h3>
            <p>{{ member.role }}</p>
            <p>{{ member.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Location Details Section -->
    <section class="location">
      <div class="container">
        <h2>{{ $t('about.location.title') }}</h2>
        <div class="location-content">
          <div class="address">
            <h3>{{ $t('about.location.address') }}</h3>
            <p>{{ $t('about.location.address_text') }}</p>
          </div>
          <div class="map-placeholder">
            <p>{{ $t('about.location.map_placeholder') }}</p>
            <!-- Placeholder for map integration -->
            <div class="map-box">
              <iframe
                src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d42834.667869695404!2d104.90503569780849!3d12.691077204948286!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x310e7300049ceb81%3A0x2d511e12556edd73!2z4Z6b4Z-S4Z6E4Z624Z6F4Z6H4Z674Z-G4Z6Y4Z634Z6P4Z-S4Z6PIC0gRnJpZW5kcyBNZWV0J3M!5e0!3m2!1skm!2skh!4v1766159877798!5m2!1skm!2skh"
                width="600" height="300" style="border:0;" allowfullscreen="" loading="lazy"
                referrerpolicy="no-referrer-when-downgrade"></iframe>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
// Import images
import heroImage from '../assets/3342857.jpg'
import bigImg from '../assets/members/big.jpg'
import headImg from '../assets/members/head.jpg'
import auntImg from '../assets/members/aunt.jpg'
import phouImg from '../assets/members/phou.jpg'

export default {
  name: 'About',
  computed: {
    teamMembers() {
      return [
        {
          name: this.$t('about.team.members.0.name'),
          role: this.$t('about.team.members.0.role'),
          description: this.$t('about.team.members.0.description'),
          photo: bigImg
        },
        {
          name: this.$t('about.team.members.1.name'),
          role: this.$t('about.team.members.1.role'),
          description: this.$t('about.team.members.1.description'),
          photo: headImg
        },
        {
          name: this.$t('about.team.members.2.name'),
          role: this.$t('about.team.members.2.role'),
          description: this.$t('about.team.members.2.description'),
          photo: auntImg
        },
        {
          name: this.$t('about.team.members.3.name'),
          role: this.$t('about.team.members.3.role'),
          description: this.$t('about.team.members.3.description'),
          photo: phouImg
        }
      ]
    }
  }
}
</script>

<style scoped>
.about {
  justify-content: center;
  /* Inherits global font */
}

.hero {
  height: 50vh;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  text-align: center;
  position: relative;
}

.hero::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(109, 216, 92, 0.3), rgba(53, 92, 54, 0.3));
}

.hero-content {
  position: relative;
  z-index: 1;
}

.hero-content h1 {
  font-size: 3.5rem;
  margin-bottom: var(--spacing-medium);
  text-shadow: 2px 2px 4px var(--shadow);
}

.hero-content p {
  font-size: 1.3rem;
  margin: 0;
}

.story,
.team,
.location {
  padding: var(--spacing-large) 0;
}

.story {
  background: var(--accent-color);
}

.team {
  background: white;
}

.location {
  background: var(--accent-color);
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--spacing-large);
}

.story h2,
.team h2,
.location h2 {
  text-align: center;
  margin-bottom: var(--spacing-large);
  color: var(--secondary-color);
}

.story p {
  font-size: 1.1rem;
  line-height: 1.6;
  margin-bottom: var(--spacing-medium);
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
  text-align: center;
}

.team-members {
  display: grid;
  grid-template-columns: 1fr;
  /* Mobile: 1 column */
  gap: var(--spacing-large);
  justify-items: center;
}

.member {
  background: white;
  border-radius: var(--border-radius);
  padding: var(--spacing-large);
  text-align: center;
  box-shadow: 0 4px 8px var(--shadow);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  max-width: 300px;
}

.member:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 16px var(--shadow);
}

.member-photo {
  width: 150px;
  height: 150px;
  background-size: cover;
  background-position: center;
  border-radius: 50%;
  margin: 0 auto var(--spacing-medium);
  border: 4px solid var(--primary-color);
}

.member h3 {
  font-size: 1.5rem;
  margin: 0 0 var(--spacing-small) 0;
  color: var(--text-color);
}

.member p:first-of-type {
  font-weight: 600;
  color: var(--primary-color);
  margin: 0 0 var(--spacing-small) 0;
}

.member p:last-of-type {
  color: #666;
  margin: 0;
}

.location-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--spacing-large);
  align-items: start;
}

.address,
.map-placeholder {
  background: white;
  border-radius: var(--border-radius);
  padding: var(--spacing-large);
  box-shadow: 0 4px 8px var(--shadow);
}

.address h3,
.map-placeholder p {
  font-size: 1.5rem;
  margin-bottom: var(--spacing-medium);
  color: var(--secondary-color);
}

.map-box {
  width: 100%;
  height: 250px;
  background-color: #f0f0f0;
  border: 1px solid #ccc;
  border-radius: var(--border-radius);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2rem;
  color: #666;
}

/* Responsive Design - Mobile First */
@media (min-width: 768px) {
  .hero-content h1 {
    font-size: 3rem;
  }

  .hero-content p {
    font-size: 1.2rem;
  }

  .story p {
    text-align: center;
  }

  .team-members {
    grid-template-columns: repeat(2, 1fr);
    /* Tablet: 2 columns */
  }

  .location-content {
    grid-template-columns: 1fr 1fr;
  }
}

@media (min-width: 1024px) {
  .hero-content h1 {
    font-size: 3.5rem;
  }

  .hero-content p {
    font-size: 1.3rem;
  }

  .team-members {
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    /* Desktop: 3 columns */
  }
}
</style>