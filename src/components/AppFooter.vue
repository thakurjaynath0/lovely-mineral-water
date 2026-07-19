<script setup>
const year = new Date().getFullYear()
</script>

<template>
  <footer class="footer">
    <div class="container footer-grid">
      <div class="footer-brand">
        <span class="brand-text">Lovely <strong>Mineral Water Supply</strong></span>
        <p>Pure water, delivered to your doorstep — the same day, every time.</p>
      </div>

      <div class="footer-col">
        <h4>Quick links</h4>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/contact">Contact</RouterLink>
      </div>

      <div class="footer-col">
        <h4>Reach us</h4>
        <a href="tel:+910000000000">+91 70220 19420</a>
        <a href="mailto:hello@lovelymineralwater.in">hello@lovelymineralwater.in</a>
        <span>7:00 AM – 9:00 PM, all days</span>
      </div>
    </div>
    <div class="container footer-bottom">
      <span>© {{ year }} Lovely Mineral Water Supply. All rights reserved.</span>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background: var(--teal-900);
  color: rgba(255, 255, 255, 0.85);
  margin-top: 100px;
  padding-top: 56px;
}

.footer-grid {
  display: grid;
  grid-template-columns: 1.4fr 1fr 1fr;
  gap: 32px;
  padding-bottom: 36px;
}

.brand-text {
  font-family: var(--font-display);
  font-size: 1.15rem;
  color: #fff;
}

.footer-brand p {
  margin-top: 12px;
  font-size: 0.92rem;
  max-width: 30ch;
  color: rgba(255, 255, 255, 0.65);
}

.footer-col {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.footer-col h4 {
  font-family: var(--font-body);
  font-size: 0.78rem;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--cyan-500);
  margin-bottom: 4px;
}

.footer-col a,
.footer-col span {
  font-size: 0.92rem;
  color: rgba(255, 255, 255, 0.78);
}

.footer-col a:hover {
  color: #fff;
}

.footer-bottom {
  border-top: 1px solid rgba(255, 255, 255, 0.12);
  padding: 18px 24px;
  font-size: 0.8rem;
  color: rgba(255, 255, 255, 0.55);
}

@media (max-width: 700px) {
  .footer-grid {
    grid-template-columns: 1fr;
  }
}
</style>
