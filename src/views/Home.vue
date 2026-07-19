<script setup>
const steps = [
  {
    n: '01',
    title: 'You call or WhatsApp',
    desc: 'Tell us how many cans you need. No app, no signup — just a quick call.'
  },
  {
    n: '02',
    title: 'We fill & test fresh',
    desc: 'Every can is RO-purified and quality-checked before it leaves our plant.'
  },
  {
    n: '03',
    title: 'Delivered to your door',
    desc: 'Our rider brings it straight to your doorstep, usually within 30 minutes.'
  }
]

const badges = [
  { label: '100% RO Purified', icon: 'drop' },
  { label: 'Delivery in 30 minutes', icon: 'truck' },
  { label: 'Sealed & Tamper-Proof', icon: 'shield' },
  { label: 'Fair, Fixed Pricing', icon: 'tag' }
]
</script>

<template>
  <!-- Hero -->
  <section class="hero">
    <div class="container hero-grid">
      <div class="hero-copy">
        <span class="eyebrow">Doorstep can delivery</span>
        <h1>
          Clean water,<br />
          <span class="highlight">delivered</span> before<br />
          your jug runs dry.
        </h1>
        <p class="lede">
          Lovely Mineral Water Supply fills, tests and delivers 20L mineral
          water cans straight to your home or office — reliably, and on time.
        </p>
        <div class="hero-actions">
          <a href="tel:+910000000000" class="btn btn-primary">Order a Can Now</a>
          <RouterLink to="/contact" class="btn btn-outline">Get in Touch</RouterLink>
        </div>
        <div class="hero-trust">
          <div class="avatar-stack" aria-hidden="true">
            <span></span><span></span><span></span>
          </div>
          <p>Trusted by <strong>500+ homes</strong> in the neighbourhood</p>
        </div>
      </div>

      <div class="hero-visual">
        <div class="hero-image-frame">
          <img
            src="https://cf-images.assettype.com/TNIE%2Fimport%2F2020%2F3%2F24%2Foriginal%2FWater.jpg?w=1024&auto=format%2Ccompress&fit=max"
            alt="Stacked mineral water cans ready for delivery"
            loading="eager"
          />
        </div>
        <div class="floating-card">
          <svg width="22" height="22" viewBox="0 0 24 24" fill="none"><path d="M12 2C12 2 5 11.4 5 15.7A7 7 0 0 0 19 15.7C19 11.4 12 2 12 2Z" fill="#2BB6C4"/></svg>
          <div>
            <strong>20L Can</strong>
            <span>Refilled &amp; sealed today</span>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Trust badges -->
  <section class="badges">
    <div class="container badges-row">
      <div class="badge" v-for="b in badges" :key="b.label">
        <svg v-if="b.icon === 'drop'" width="20" height="20" viewBox="0 0 24 24" fill="none"><path d="M12 2C12 2 5 11.4 5 15.7A7 7 0 0 0 19 15.7C19 11.4 12 2 12 2Z" fill="#2BB6C4"/></svg>
        <svg v-else-if="b.icon === 'truck'" width="20" height="20" viewBox="0 0 24 24" fill="none"><path d="M2 7h11v9H2z" fill="#2BB6C4"/><path d="M13 10h4l3 3v3h-7z" fill="#0B5D6B"/><circle cx="6" cy="18" r="1.6" fill="#093840"/><circle cx="16.5" cy="18" r="1.6" fill="#093840"/></svg>
        <svg v-else-if="b.icon === 'shield'" width="20" height="20" viewBox="0 0 24 24" fill="none"><path d="M12 2l7 3v6c0 5-3.4 8.4-7 11-3.6-2.6-7-6-7-11V5l7-3Z" fill="#2BB6C4"/></svg>
        <svg v-else width="20" height="20" viewBox="0 0 24 24" fill="none"><path d="M3 12l9-9h9v9l-9 9-9-9Z" fill="#2BB6C4"/><circle cx="15" cy="9" r="1.6" fill="#093840"/></svg>
        <span>{{ b.label }}</span>
      </div>
    </div>
  </section>

  <!-- How it works -->
  <section class="process">
    <div class="container">
      <span class="eyebrow">How delivery works</span>
      <h2>From our plant to your kitchen, in three stops.</h2>

      <div class="process-track">
        <svg class="track-line" viewBox="0 0 1000 40" preserveAspectRatio="none" aria-hidden="true">
          <line x1="60" y1="20" x2="940" y2="20" stroke="#2BB6C4" stroke-width="2.5" stroke-dasharray="2 14" stroke-linecap="round"/>
        </svg>
        <div class="process-step" v-for="s in steps" :key="s.n">
          <span class="step-n">{{ s.n }}</span>
          <h3>{{ s.title }}</h3>
          <p>{{ s.desc }}</p>
        </div>
      </div>
    </div>
  </section>

  <!-- Products -->
  <section class="products">
    <div class="container">
      <span class="eyebrow">What we supply</span>
      <h2>Simple options, honest pricing.</h2>

      <div class="product-grid">
        <div class="product-card">
          <div class="product-media can-20">
            <svg viewBox="0 0 120 160" width="88" height="118" aria-hidden="true">
              <rect x="30" y="18" width="60" height="128" rx="14" fill="#E3F6F8" stroke="#2BB6C4" stroke-width="3"/>
              <rect x="46" y="4" width="28" height="20" rx="6" fill="#2BB6C4"/>
              <path d="M40 60c8 10 32 10 40 0" stroke="#0B5D6B" stroke-width="3" fill="none" stroke-linecap="round"/>
            </svg>
          </div>
          <h3>20L Mineral Water Can</h3>
          <p>Our most popular size — perfect for daily household drinking &amp; cooking needs.</p>
          <div class="product-price">₹40 <span>/ can, refill</span></div>
        </div>

        <div class="product-card">
          <div class="product-media can-office">
            <svg viewBox="0 0 120 160" width="88" height="118" aria-hidden="true">
              <rect x="26" y="14" width="68" height="132" rx="14" fill="#E3F6F8" stroke="#0B5D6B" stroke-width="3"/>
              <rect x="44" y="0" width="32" height="20" rx="6" fill="#0B5D6B"/>
              <path d="M38 56c10 12 34 12 44 0" stroke="#2BB6C4" stroke-width="3" fill="none" stroke-linecap="round"/>
              <path d="M38 76c10 12 34 12 44 0" stroke="#2BB6C4" stroke-width="3" fill="none" stroke-linecap="round"/>
            </svg>
          </div>
          <h3>Office &amp; Bulk Supply</h3>
          <p>Weekly scheduled delivery for offices, shops and events. Volume discounts available.</p>
          <div class="product-price">Custom <span>plan</span></div>
        </div>

        <div class="product-card">
          <div class="product-media dispenser">
            <svg viewBox="0 0 120 160" width="88" height="118" aria-hidden="true">
              <rect x="34" y="10" width="52" height="60" rx="10" fill="#2BB6C4" opacity="0.25"/>
              <rect x="24" y="70" width="72" height="76" rx="10" fill="#E3F6F8" stroke="#0B5D6B" stroke-width="3"/>
              <circle cx="46" cy="98" r="5" fill="#0B5D6B"/>
              <circle cx="74" cy="98" r="5" fill="#F0A234"/>
            </svg>
          </div>
          <h3>Dispenser on Rent</h3>
          <p>Hot &amp; cold dispenser rental with free maintenance — pair it with your can subscription.</p>
          <div class="product-price">₹150 <span>/ month</span></div>
        </div>
      </div>
    </div>
  </section>

  <!-- CTA banner -->
  <section class="cta-banner">
    <div class="container cta-inner">
      <div>
        <h2>Running low on water?</h2>
        <p>Call, WhatsApp, or drop us a message — your can will be at the door within 30 minutes.</p>
      </div>
      <div class="cta-actions">
        <a href="tel:+910000000000" class="btn btn-primary">Call +91 70220 19420</a>
        <RouterLink to="/contact" class="btn btn-ghost">Message Us</RouterLink>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  padding: 64px 0 40px;
  overflow: hidden;
  position: relative;
}

.hero::before {
  content: '';
  position: absolute;
  top: -140px;
  right: -160px;
  width: 480px;
  height: 480px;
  border-radius: 50%;
  background: radial-gradient(circle, var(--cyan-100), transparent 70%);
  z-index: -1;
}

.hero-grid {
  display: grid;
  grid-template-columns: 1.05fr 0.95fr;
  gap: 48px;
  align-items: center;
}

h1 {
  font-size: clamp(2.4rem, 4.6vw, 3.6rem);
  color: var(--teal-900);
  margin-top: 18px;
}

.highlight {
  color: var(--teal-700);
  position: relative;
}

.lede {
  margin-top: 20px;
  font-size: 1.08rem;
  color: rgba(11, 46, 51, 0.72);
  max-width: 46ch;
}

.hero-actions {
  display: flex;
  gap: 14px;
  margin-top: 30px;
  flex-wrap: wrap;
}

.hero-trust {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-top: 34px;
}

.hero-trust p {
  font-size: 0.9rem;
  color: rgba(11, 46, 51, 0.7);
}

.avatar-stack {
  display: flex;
}

.avatar-stack span {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  border: 2px solid var(--bg);
  margin-left: -10px;
  background: linear-gradient(135deg, var(--cyan-500), var(--teal-700));
}

.avatar-stack span:first-child {
  margin-left: 0;
}

.hero-visual {
  position: relative;
}

.hero-image-frame {
  border-radius: var(--radius-lg);
  overflow: hidden;
  box-shadow: 0 30px 60px -28px rgba(9, 56, 64, 0.45);
  aspect-ratio: 4 / 3.1;
}

.hero-image-frame img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.floating-card {
  position: absolute;
  bottom: -26px;
  left: -18px;
  background: var(--surface);
  border-radius: var(--radius-md);
  padding: 14px 18px;
  display: flex;
  align-items: center;
  gap: 12px;
  box-shadow: 0 18px 36px -18px rgba(9, 56, 64, 0.35);
}

.floating-card div {
  display: flex;
  flex-direction: column;
  line-height: 1.25;
}

.floating-card strong {
  font-size: 0.9rem;
  color: var(--teal-900);
}

.floating-card span {
  font-size: 0.76rem;
  color: rgba(11, 46, 51, 0.6);
}

/* Badges */
.badges {
  margin-top: 56px;
}

.badges-row {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 18px;
  padding: 22px 28px;
  background: var(--surface);
  border-radius: var(--radius-md);
  border: 1px solid var(--line);
}

.badge {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 0.88rem;
  font-weight: 600;
  color: var(--teal-900);
}

/* Process */
.process {
  padding: 100px 0 40px;
}

.process h2 {
  font-size: clamp(1.7rem, 3vw, 2.3rem);
  margin-top: 10px;
  max-width: 24ch;
  color: var(--teal-900);
}

.process-track {
  position: relative;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 32px;
  margin-top: 56px;
}

.track-line {
  position: absolute;
  top: -30px;
  left: 0;
  width: 100%;
  height: 40px;
}

.process-step {
  background: var(--surface);
  border: 1px solid var(--line);
  border-radius: var(--radius-md);
  padding: 28px 24px;
}

.step-n {
  font-family: var(--font-display);
  font-size: 1.6rem;
  color: var(--cyan-500);
}

.process-step h3 {
  font-size: 1.08rem;
  margin-top: 10px;
  color: var(--teal-900);
}

.process-step p {
  margin-top: 10px;
  font-size: 0.92rem;
  color: rgba(11, 46, 51, 0.68);
}

/* Products */
.products {
  padding: 90px 0 20px;
}

.products h2 {
  font-size: clamp(1.7rem, 3vw, 2.3rem);
  margin-top: 10px;
  color: var(--teal-900);
}

.product-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 26px;
  margin-top: 46px;
}

.product-card {
  background: var(--surface);
  border-radius: var(--radius-md);
  border: 1px solid var(--line);
  padding: 30px 26px;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.product-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 20px 40px -24px rgba(9, 56, 64, 0.3);
}

.product-media {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 150px;
  background: var(--cyan-100);
  border-radius: var(--radius-sm);
  margin-bottom: 20px;
}

.product-card h3 {
  font-size: 1.1rem;
  color: var(--teal-900);
}

.product-card p {
  margin-top: 10px;
  font-size: 0.9rem;
  color: rgba(11, 46, 51, 0.68);
  min-height: 60px;
}

.product-price {
  margin-top: 16px;
  font-family: var(--font-display);
  font-size: 1.5rem;
  color: var(--teal-700);
}

.product-price span {
  font-family: var(--font-body);
  font-size: 0.78rem;
  color: rgba(11, 46, 51, 0.55);
  font-weight: 500;
}

/* CTA banner */
.cta-banner {
  margin: 110px 0 0;
  background: linear-gradient(120deg, var(--teal-900), var(--teal-700));
  padding: 60px 0;
}

.cta-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 30px;
  flex-wrap: wrap;
}

.cta-inner h2 {
  color: #fff;
  font-size: clamp(1.6rem, 3vw, 2.1rem);
}

.cta-inner p {
  margin-top: 10px;
  color: rgba(255, 255, 255, 0.72);
  max-width: 42ch;
}

.cta-actions {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
}

@media (max-width: 900px) {
  .hero-grid {
    grid-template-columns: 1fr;
  }

  .hero-visual {
    order: -1;
  }

  .process-track,
  .product-grid {
    grid-template-columns: 1fr;
  }

  .track-line {
    display: none;
  }
}
</style>
