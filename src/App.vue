<script setup lang="ts">
import { onMounted, ref } from 'vue'

const isDark = ref(true)

const links = [
  {
    label: 'Portfolio',
    href: 'https://stevehering.com',
    icon: 'M14 3h7v7h-2V6.41l-9.29 9.3-1.42-1.42 9.3-9.29H14V3zM5 5h6v2H7v10h10v-4h2v6H5V5z',
  },
  {
    label: 'LinkedIn',
    href: 'https://linkedin.com/in/stevehering',
    icon: 'M4.98 3.5a2.5 2.5 0 1 1 0 5 2.5 2.5 0 0 1 0-5zM3 9h4v12H3V9zm7 0h3.8v1.71h.05c.53-.95 1.83-1.95 3.77-1.95 4.03 0 4.78 2.65 4.78 6.1V21h-4v-5.32c0-1.27-.02-2.9-1.77-2.9-1.77 0-2.04 1.38-2.04 2.81V21h-4V9z',
  },
  {
    label: 'Email',
    href: 'mailto:steve.hering@gmail.com',
    icon: 'M3 5h18a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1H3a1 1 0 0 1-1-1V6a1 1 0 0 1 1-1zm9 7.6 8-5.2V6H4v1.4l8 5.2zM4 9.79V18h16V9.79l-8 5.2-8-5.2z',
  },
]

function applyTheme() {
  document.documentElement.classList.toggle('light', !isDark.value)
}

function toggleTheme() {
  isDark.value = !isDark.value
  applyTheme()
  localStorage.setItem('theme', isDark.value ? 'dark' : 'light')
}

onMounted(() => {
  const saved = localStorage.getItem('theme')
  if (saved) isDark.value = saved === 'dark'
  applyTheme()
})
</script>

<template>
  <main class="card">
    <button
      class="theme-toggle"
      type="button"
      :aria-label="isDark ? 'Switch to light mode' : 'Switch to dark mode'"
      @click="toggleTheme"
    >
      <svg v-if="isDark" viewBox="0 0 24 24" width="18" height="18" aria-hidden="true">
        <path
          fill="currentColor"
          d="M12 3a1 1 0 0 1 1 1v2a1 1 0 1 1-2 0V4a1 1 0 0 1 1-1zm0 14a5 5 0 1 1 0-10 5 5 0 0 1 0 10zm0 2a1 1 0 0 1 1 1v2a1 1 0 1 1-2 0v-2a1 1 0 0 1 1-1zM3 12a1 1 0 0 1 1-1h2a1 1 0 1 1 0 2H4a1 1 0 0 1-1-1zm15 0a1 1 0 0 1 1-1h2a1 1 0 1 1 0 2h-2a1 1 0 0 1-1-1zM5.64 5.64a1 1 0 0 1 1.41 0l1.42 1.42a1 1 0 1 1-1.41 1.41L5.64 7.05a1 1 0 0 1 0-1.41zm9.9 9.9a1 1 0 0 1 1.41 0l1.42 1.42a1 1 0 1 1-1.41 1.41l-1.42-1.42a1 1 0 0 1 0-1.41zm2.83-9.9a1 1 0 0 1 0 1.41l-1.42 1.42a1 1 0 1 1-1.41-1.41l1.42-1.42a1 1 0 0 1 1.41 0zm-9.9 9.9a1 1 0 0 1 0 1.41l-1.42 1.42a1 1 0 1 1-1.41-1.41l1.42-1.42a1 1 0 0 1 1.41 0z"
        />
      </svg>
      <svg v-else viewBox="0 0 24 24" width="18" height="18" aria-hidden="true">
        <path
          fill="currentColor"
          d="M21 12.79A9 9 0 1 1 11.21 3a7 7 0 0 0 9.79 9.79z"
        />
      </svg>
    </button>

    <div class="avatar" aria-hidden="true">
      <svg viewBox="0 0 24 24" width="48" height="48">
        <path
          fill="currentColor"
          d="M12 12a5 5 0 1 0-5-5 5 5 0 0 0 5 5zm0 2c-4.42 0-8 2.69-8 6v2h16v-2c0-3.31-3.58-6-8-6z"
        />
      </svg>
    </div>

    <h1 class="name">Steve Hering</h1>
    <p class="bio">
      Builder, designer, and lifelong tinkerer. Working at the intersection of product,
      technology, and human experience.
    </p>

    <nav class="links">
      <a
        v-for="link in links"
        :key="link.label"
        :href="link.href"
        class="link-btn"
        target="_blank"
        rel="noopener noreferrer"
      >
        <svg class="link-icon" viewBox="0 0 24 24" width="20" height="20" aria-hidden="true">
          <path fill="currentColor" :d="link.icon" />
        </svg>
        <span>{{ link.label }}</span>
      </a>
    </nav>
  </main>
</template>

<style scoped>
.card {
  position: relative;
  width: 100%;
  max-width: 480px;
  background-color: var(--card);
  border: 1px solid var(--border);
  border-radius: 24px;
  padding: 2.5rem 2rem;
  text-align: center;
  box-shadow: var(--shadow);
  backdrop-filter: blur(8px);
  transition: background-color 0.3s ease, border-color 0.3s ease;
}

.theme-toggle {
  position: absolute;
  top: 1rem;
  right: 1rem;
  width: 36px;
  height: 36px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  color: var(--text-muted);
  background: transparent;
  border: 1px solid var(--border);
  border-radius: 50%;
  cursor: pointer;
  transition: color 0.2s ease, background-color 0.2s ease, transform 0.2s ease;
}

.theme-toggle:hover {
  color: var(--text);
  background-color: var(--card-hover);
  transform: rotate(15deg);
}

.avatar {
  width: 96px;
  height: 96px;
  margin: 0 auto 1.25rem;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--accent), #b06cff);
  color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 8px 20px rgba(108, 140, 255, 0.35);
}

.name {
  font-size: 1.75rem;
  font-weight: 700;
  letter-spacing: -0.02em;
  margin-bottom: 0.5rem;
}

.bio {
  font-size: 0.95rem;
  line-height: 1.55;
  color: var(--text-muted);
  margin-bottom: 2rem;
}

.links {
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.link-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.75rem;
  width: 100%;
  padding: 0.9rem 1rem;
  font-family: inherit;
  font-size: 1rem;
  font-weight: 600;
  color: var(--text);
  background-color: var(--bg-elev);
  border: 1px solid var(--border);
  border-radius: 14px;
  cursor: pointer;
  transition: transform 0.15s ease, background-color 0.2s ease, border-color 0.2s ease;
}

.link-btn:hover {
  background-color: var(--card-hover);
  border-color: var(--accent);
  transform: translateY(-2px);
}

.link-icon {
  color: var(--accent);
  flex-shrink: 0;
}

@media (max-width: 480px) {
  .card {
    padding: 2rem 1.25rem;
    border-radius: 20px;
  }

  .name {
    font-size: 1.5rem;
  }
}
</style>
