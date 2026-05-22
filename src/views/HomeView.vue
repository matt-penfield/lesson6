<script setup lang="ts">
const links = [
  { label: 'Portfolio', url: '#' },
  { label: 'Dribbble', url: '#' },
  { label: 'LinkedIn', url: '#' },
  { label: 'Email', url: 'mailto:hello@mattppenfield.com' },
]
</script>

<template>
  <main class="page">
    <div class="grid">
      <div class="left">
        <h1 class="name">Matt<br />Penfield</h1>
        <p class="tagline">Designer, builder, creative technologist.</p>
      </div>

      <nav class="right">
        <a
          v-for="link in links"
          :key="link.label"
          :href="link.url"
          class="link-btn"
        >
          {{ link.label }}
        </a>
      </nav>
    </div>
  </main>
</template>

<style scoped>
.page {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
}

.grid {
  display: grid;
  grid-template-columns: 1.4fr 1fr;
  gap: 4rem;
  align-items: end;
  max-width: 960px;
  width: 100%;
}

.left {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.name {
  font-size: clamp(4rem, 10vw, 9rem);
  font-weight: 700;
  line-height: 0.85;
  letter-spacing: -0.04em;
  text-transform: uppercase;
}

.tagline {
  font-size: 1.1rem;
  font-weight: 300;
  letter-spacing: 0.02em;
  max-width: 280px;
  border-top: 2px solid var(--black);
  padding-top: 1rem;
}

.right {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.link-btn {
  display: block;
  padding: 1rem 1.5rem;
  border: 2px solid var(--black);
  text-decoration: none;
  color: var(--black);
  font-size: 1rem;
  font-weight: 500;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  transition: background 0.15s, color 0.15s;
}

.link-btn:hover {
  background: var(--black);
  color: var(--white);
}

@media (max-width: 680px) {
  .grid {
    grid-template-columns: 1fr;
    gap: 3rem;
    align-items: start;
  }

  .name {
    font-size: clamp(3rem, 14vw, 5rem);
  }
}
</style>
