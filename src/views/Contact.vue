<script setup>
import { reactive, ref } from 'vue'

const WEB3FORMS_ACCESS_KEY = "edbf8567-c8d7-4579-8c5b-15e17fef7a95"

const form = reactive({
  name: '',
  email: '',
  phone: '',
  address: '',
  cans: '1',
  message: ''
})

const sent = ref(false)
const submitting = ref(false)
const error = ref('')

async function submitOrder() {
  if (!WEB3FORMS_ACCESS_KEY) {
    error.value = 'Web3Forms access key is not configured. Add VITE_WEB3FORMS_ACCESS_KEY to your .env file.'
    return
  }

  submitting.value = true
  error.value = ''

  try {
    const response = await fetch('https://api.web3forms.com/submit', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        access_key: WEB3FORMS_ACCESS_KEY,
        subject: `New Contact Request from ${form.name || 'Website Visitor'}`,
        from_name: 'Lovely Mineral Water Supply - Contact Form',
        name: form.name,
        phone: form.phone,
        email: form.email,
        address: form.address || 'Not provided',
        message: form.message || 'No message provided'
      })
    })

    const data = await response.json()

    if (!response.ok || data.success === false) {
      throw new Error(data.error?.message || 'Unable to send request. Please try again.')
    }

    sent.value = true
  } catch (err) {
    error.value = err instanceof Error ? err.message : 'Request failed. Please try again.'
  } finally {
    submitting.value = false
  }
}
</script>

<template>
  <section class="page-header">
    <div class="container">
      <span class="eyebrow">We're here to help</span>
      <h1>Let's get water to your door.</h1>
      <p>Call us for an instant order, or send your details and we'll ring you back.</p>
    </div>
  </section>

  <section class="contact-section">
    <div class="container contact-grid">
      <!-- Contact info -->
      <div class="info-card">
        <h2>Contact details</h2>

        <div class="info-row">
          <div class="icon-badge">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M6.6 10.8c1.4 2.8 3.8 5.1 6.6 6.6l2.2-2.2c.3-.3.7-.4 1-.2 1.1.4 2.3.6 3.6.6.6 0 1 .4 1 1V20c0 .6-.4 1-1 1C10.5 21 3 13.5 3 4c0-.6.4-1 1-1h3.4c.6 0 1 .4 1 1 0 1.3.2 2.5.6 3.6.1.3 0 .7-.2 1L6.6 10.8Z" fill="#2BB6C4"/></svg>
          </div>
          <div>
            <h3>Phone / WhatsApp</h3>
            <a href="tel:+917022019420">+91 70220 19420, +91 91087 03403</a>
          </div>
        </div>

        <div class="info-row">
          <div class="icon-badge">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M4 6.5A2.5 2.5 0 0 1 6.5 4h11A2.5 2.5 0 0 1 20 6.5v11a2.5 2.5 0 0 1-2.5 2.5h-11A2.5 2.5 0 0 1 4 17.5v-11Z" stroke="#0B5D6B" stroke-width="1.6"/><path d="m5 7 7 5 7-5" stroke="#0B5D6B" stroke-width="1.6" stroke-linecap="round"/></svg>
          </div>
          <div>
            <h3>Email</h3>
            <a href="mailto:lovelybk96@gmail.com">lovelybk96@gmail.com</a>
          </div>
        </div>

        <div class="info-row">
          <div class="icon-badge">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><path d="M12 21s7-6.3 7-11.5A7 7 0 0 0 5 9.5C5 14.7 12 21 12 21Z" fill="#2BB6C4"/></svg>
          </div>
          <div>
            <h3>Address</h3>
            <p>1st Main Rd, 1st cross, Venkateshwara Layout, S.G. Palya, Bengaluru, Karnataka 560029</p>
          </div>
        </div>

        <div class="info-row">
          <div class="icon-badge">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none"><circle cx="12" cy="12" r="8.5" stroke="#0B5D6B" stroke-width="1.6"/><path d="M12 7.5V12l3 2" stroke="#0B5D6B" stroke-width="1.6" stroke-linecap="round"/></svg>
          </div>
          <div>
            <h3>Delivery hours</h3>
            <p>Opens 24 hours, all days of the week</p>
          </div>
        </div>

        <div class="map-frame">
          <iframe
            title="Service area map"
              src="https://www.google.com/maps?q=1st%20Main%20Rd%2C%201st%20cross%2C%20Venkateshwara%20Layout%2C%20S.G.%20Palya%2C%20Bengaluru%2C%20Karnataka%20560029&output=embed"
            width="100%"
            height="220"
            style="border:0"
            loading="lazy"
            referrerpolicy="no-referrer-when-downgrade"
          ></iframe>
        </div>
      </div>

      <!-- Order form -->
      <div class="form-card">
        <h2>Request a delivery</h2>
        <p class="form-sub">Fill this in and our team will call to confirm your order.</p>

        <form v-if="!sent" @submit.prevent="submitOrder">
          <div class="field">
            <label for="name">Your name</label>
            <input id="name" v-model="form.name" type="text" placeholder="e.g. Priya Raman" required />
          </div>

          <div class="field">
            <label for="email">Email address (optional)</label>
            <input id="email" v-model="form.email" type="email" placeholder="e.g. example@email.com" />
          </div>

          <div class="field">
            <label for="phone">Phone number</label>
            <input id="phone" v-model="form.phone" type="tel" placeholder="e.g. 98765 43210" required />
          </div>

          <div class="field">
            <label for="address">Delivery address</label>
            <textarea id="address" v-model="form.address" rows="3" placeholder="Flat / house no., street, area" required></textarea>
          </div>

          <div class="field">
            <label for="cans">Number of cans</label>
            <select id="cans" v-model="form.cans">
              <option value="1">1 can</option>
              <option value="2">2 cans</option>
              <option value="3">3 cans</option>
              <option value="5+">5+ cans (bulk)</option>
            </select>
          </div>

          <div class="field">
            <label for="message">Notes (optional)</label>
            <textarea id="message" v-model="form.message" rows="2" placeholder="Preferred delivery time, landmark, etc."></textarea>
          </div>

          <button type="submit" class="btn btn-primary submit-btn" :disabled="submitting">
            {{ submitting ? 'Sending...' : 'Send Request' }}
          </button>

          <p v-if="error" class="error-note">{{ error }}</p>
        </form>

        <div v-else class="success-note">
          <svg width="26" height="26" viewBox="0 0 24 24" fill="none"><circle cx="12" cy="12" r="10" fill="#2BB6C4"/><path d="m8 12.5 2.5 2.5L16 9.5" stroke="#fff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg>
          <div>
            <h3>Thanks, {{ form.name || 'there' }}!</h3>
            <p>We've noted your request for {{ form.cans }} can(s). Our team will call you shortly on {{ form.phone }} to confirm.</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.page-header {
  padding: 60px 0 20px;
}

.page-header h1 {
  font-size: clamp(2rem, 3.6vw, 2.8rem);
  margin-top: 14px;
  color: var(--teal-900);
}

.page-header p {
  margin-top: 12px;
  color: rgba(11, 46, 51, 0.68);
  max-width: 50ch;
}

.contact-section {
  padding: 40px 0 100px;
}

.contact-grid {
  display: grid;
  grid-template-columns: 0.9fr 1.1fr;
  gap: 28px;
  align-items: start;
}

.info-card,
.form-card {
  background: var(--surface);
  border: 1px solid var(--line);
  border-radius: var(--radius-md);
  padding: 32px;
}

.info-card h2,
.form-card h2 {
  font-size: 1.3rem;
  color: var(--teal-900);
}

.form-sub {
  margin-top: 8px;
  font-size: 0.9rem;
  color: rgba(11, 46, 51, 0.6);
}

.info-row {
  display: flex;
  gap: 14px;
  margin-top: 24px;
  align-items: flex-start;
}

.icon-badge {
  width: 38px;
  height: 38px;
  border-radius: 50%;
  background: var(--cyan-100);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.info-row h3 {
  font-size: 0.92rem;
  color: var(--teal-900);
  font-family: var(--font-body);
  font-weight: 600;
}

.info-row a,
.info-row p {
  display: block;
  margin-top: 3px;
  font-size: 0.9rem;
  color: rgba(11, 46, 51, 0.68);
}

.info-row a:hover {
  color: var(--teal-700);
}

.map-frame {
  margin-top: 26px;
  border-radius: var(--radius-sm);
  overflow: hidden;
  border: 1px solid var(--line);
}

/* Form */
.field {
  margin-top: 18px;
  display: flex;
  flex-direction: column;
  gap: 6px;
}

.field label {
  font-size: 0.82rem;
  font-weight: 600;
  color: var(--teal-900);
}

.field input,
.field select,
.field textarea {
  font-family: var(--font-body);
  font-size: 0.94rem;
  padding: 11px 14px;
  border-radius: var(--radius-sm);
  border: 1.4px solid var(--line);
  background: var(--bg);
  color: var(--ink);
  resize: vertical;
}

.field input:focus,
.field select:focus,
.field textarea:focus {
  outline: none;
  border-color: var(--cyan-500);
}

.submit-btn {
  margin-top: 24px;
  width: 100%;
}

.success-note {
  margin-top: 20px;
  display: flex;
  gap: 14px;
  align-items: flex-start;
  background: var(--cyan-100);
  padding: 20px;
  border-radius: var(--radius-sm);
}

.success-note h3 {
  font-size: 1rem;
  color: var(--teal-900);
}

.success-note p {
  margin-top: 6px;
  font-size: 0.9rem;
  color: rgba(11, 46, 51, 0.72);
}

@media (max-width: 860px) {
  .contact-grid {
    grid-template-columns: 1fr;
  }
}
</style>
