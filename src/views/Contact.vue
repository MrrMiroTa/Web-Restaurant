<template>
  <div class="contact">
    <h1>{{ $t('contact.title') }}</h1>

    <!-- Contact Form -->
    <form @submit.prevent="submitForm" class="contact-form">
      <div class="form-group">
        <label for="name">{{ $t('contact.form.name_label') }}</label>
        <input id="name" v-model="form.name" type="text" required class="form-input" />
        <span v-if="errors.name" class="error">{{ errors.name }}</span>
      </div>

      <div class="form-group">
        <label for="email">{{ $t('contact.form.email_label') }}</label>
        <input id="email" v-model="form.email" type="email" required class="form-input" />
        <span v-if="errors.email" class="error">{{ errors.email }}</span>
      </div>

      <div class="form-group">
        <label for="phone">{{ $t('contact.form.phone_label') }}</label>
        <input id="phone" v-model="form.phone" type="tel" class="form-input" />
      </div>

      <div class="form-group">
        <label for="message">{{ $t('contact.form.message_label') }}</label>
        <textarea id="message" v-model="form.message" required class="form-textarea"></textarea>
        <span v-if="errors.message" class="error">{{ errors.message }}</span>
      </div>

      <button type="submit" class="submit-btn">{{ $t('contact.form.send_message') }}</button>
    </form>

    <!-- Restaurant Contact Info -->
    <section class="contact-info">
      <h2>{{ $t('contact.info.title') }}</h2>
      <p><strong>{{ $t('contact.info.address_label') }}</strong> {{ $t('contact.info.address_value') }}</p>
      <p><strong>{{ $t('contact.info.phone_label') }}</strong> {{ $t('contact.info.phone_value') }}</p>
      <p><strong>{{ $t('contact.info.hours_label') }}</strong> {{ $t('contact.info.hours_value') }}</p>
    </section>

    <!-- Embedded Map Placeholder -->
    <section class="map-placeholder">
      <h2>{{ $t('contact.map.title') }}</h2>
      <div class="map">
        <!-- Placeholder for embedded map -->
        <iframe
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d42834.667869695404!2d104.90503569780849!3d12.691077204948286!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x310e7300049ceb81%3A0x2d511e12556edd73!2z4Z6b4Z-S4Z6E4Z624Z6F4Z6H4Z674Z-G4Z6Y4Z634Z6P4Z-S4Z6PIC0gRnJpZW5kcyBNZWV0J3M!5e0!3m2!1skm!2skh!4v1766159877798!5m2!1skm!2skh"
          width="900" height="300" style="border:0;" allowfullscreen="" loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"></iframe>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, reactive, computed } from 'vue'
import { useI18n } from 'vue-i18n'

const { t } = useI18n()

const form = reactive({
  name: '',
  email: '',
  phone: '',
  message: ''
})

const errors = ref({})

const validateForm = () => {
  errors.value = {}
  if (!form.name.trim()) {
    errors.value.name = t('contact.form.errors.name_required')
  }
  if (!form.email.trim()) {
    errors.value.email = t('contact.form.errors.email_required')
  } else if (!/\S+@\S+\.\S+/.test(form.email)) {
    errors.value.email = t('contact.form.errors.email_invalid')
  }
  if (!form.message.trim()) {
    errors.value.message = t('contact.form.errors.message_required')
  }
  return Object.keys(errors.value).length === 0
}

const submitForm = () => {
  if (validateForm()) {
    // Handle form submission (e.g., send to API)
    alert(t('contact.form.success'))
    // Reset form
    Object.keys(form).forEach(key => {
      form[key] = ''
    })
  }
}
</script>

<style scoped>
.contact {
  max-width: 1000px;
  margin: 0 auto;
  padding: var(--spacing-medium);
}

.contact h1 {
  text-align: center;
  color: var(--secondary-color);
  margin-bottom: var(--spacing-large);
}

.contact-form {
  background: white;
  border-radius: var(--border-radius);
  padding: var(--spacing-large);
  box-shadow: 0 4px 8px var(--shadow);
  margin-bottom: var(--spacing-large);
}

.form-group {
  margin-bottom: var(--spacing-large);
}

.form-group label {
  display: block;
  margin-bottom: var(--spacing-small);
  font-weight: 600;
  color: var(--text-color);
}

.form-input,
.form-textarea {
  width: 100%;
  padding: var(--spacing-medium);
  border: 2px solid #e0e0e0;
  border-radius: var(--border-radius);
  font-size: 1rem;
  font-family: var(--font-family-body);
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
}

.form-input:focus,
.form-textarea:focus {
  outline: none;
  border-color: var(--primary-color);
  box-shadow: 0 0 0 3px rgba(255, 107, 53, 0.1);
}

.form-textarea {
  height: 120px;
  resize: vertical;
}

.submit-btn {
  background: var(--primary-color);
  color: white;
  padding: var(--spacing-medium) var(--spacing-large);
  border: none;
  border-radius: var(--border-radius);
  cursor: pointer;
  font-size: 1rem;
  font-weight: 600;
  transition: background-color 0.3s ease, transform 0.3s ease;
  width: 100%;
}

.submit-btn:hover {
  background: var(--secondary-color);
  transform: translateY(-2px);
}

.error {
  color: var(--secondary-color);
  font-size: 0.9rem;
  margin-top: var(--spacing-small);
}

.contact-info,
.map-placeholder {
  background: var(--accent-color);
  border-radius: var(--border-radius);
  padding: var(--spacing-large);
  margin-bottom: var(--spacing-large);
  box-shadow: 0 4px 8px var(--shadow);
}

.contact-info h2,
.map-placeholder h2 {
  color: var(--secondary-color);
  margin-bottom: var(--spacing-medium);
  text-align: center;
}

.contact-info p {
  margin-bottom: var(--spacing-small);
  text-align: center;
}

.map {
  height: 300px;
  background-image: url('https://source.unsplash.com/random?map');
  background-size: cover;
  background-position: center;
  border-radius: var(--border-radius);
  display: flex;
  align-items: center;
  justify-content: center;
  border: 2px solid #e0e0e0;
  font-size: 1.1rem;
  color: #666;
}

/* Responsive Design - Mobile First */
@media (min-width: 768px) {
  .contact {
    padding: var(--spacing-large);
  }

  .contact-form {
    padding: var(--spacing-large);
  }

  .contact-info,
  .map-placeholder {
    padding: var(--spacing-large);
  }
}

@media (min-width: 1024px) {
  /* Additional desktop adjustments if needed */
}
</style>