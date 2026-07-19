<script setup>
import { ref } from 'vue'

const open = ref(false)
</script>

<template>
  <header class="nav">
    <div class="container nav-inner">
      <RouterLink to="/" class="brand" @click="open = false">
        <svg width="34" height="34" viewBox="0 0 24 24" fill="none" aria-hidden="true">
          <path d="M12 2C12 2 4.5 11.4 4.5 15.7A7.5 7.5 0 0 0 19.5 15.7C19.5 11.4 12 2 12 2Z" fill="#2BB6C4"/>
          <path d="M8.3 15.2C8.3 16.9 9.9 18.3 11.9 18.3" stroke="#E3F6F8" stroke-width="1.4" stroke-linecap="round"/>
        </svg>
        <span class="brand-text">
          <strong>Lovely</strong>
          <small>Mineral Water Supply</small>
        </span>
      </RouterLink>

      <nav class="links" :class="{ open }">
        <RouterLink to="/" @click="open = false">Home</RouterLink>
        <RouterLink to="/contact" @click="open = false">Contact</RouterLink>
        <a class="btn btn-primary call-btn" href="tel:+917022019420">Call to Order</a>
      </nav>

      <button class="burger" @click="open = !open" :aria-expanded="open" aria-label="Toggle menu">
        <span></span><span></span><span></span>
      </button>
    </div>
  </header>
</template>

<style scoped>
.nav {
  position: sticky;
  top: 0;
  z-index: 40;
  background: rgba(246, 251, 251, 0.85);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid var(--line);
}

.nav-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 76px;
}

.brand {
  display: flex;
  align-items: center;
  gap: 10px;
}

.brand-text {
  display: flex;
  flex-direction: column;
  line-height: 1.1;
}

.brand-text strong {
  font-family: var(--font-display);
  font-size: 1.2rem;
  color: var(--teal-900);
}

.brand-text small {
  font-size: 0.68rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--teal-700);
  font-weight: 600;
}

.links {
  display: flex;
  align-items: center;
  gap: 30px;
}

.links a:not(.call-btn) {
  font-weight: 600;
  font-size: 0.95rem;
  color: var(--ink);
  position: relative;
  padding: 4px 0;
}

.links a.router-link-exact-active:not(.call-btn) {
  color: var(--teal-700);
}

.links a:not(.call-btn)::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -4px;
  width: 0;
  height: 2px;
  background: var(--amber-500);
  transition: width 0.2s ease;
}

.links a:not(.call-btn):hover::after,
.links a.router-link-exact-active:not(.call-btn)::after {
  width: 100%;
}

.call-btn {
  padding: 10px 20px;
  font-size: 0.88rem;
}

.burger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  padding: 8px;
}

.burger span {
  width: 22px;
  height: 2px;
  background: var(--teal-900);
  border-radius: 2px;
}

@media (max-width: 760px) {
  .burger {
    display: flex;
  }

  .links {
    position: absolute;
    top: 76px;
    left: 0;
    right: 0;
    background: var(--surface);
    flex-direction: column;
    align-items: flex-start;
    gap: 18px;
    padding: 22px 24px 28px;
    border-bottom: 1px solid var(--line);
    display: none;
  }

  .links.open {
    display: flex;
  }

  .call-btn {
    align-self: flex-start;
  }
}
</style>
