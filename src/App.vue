<script setup>
import { ref } from 'vue'

const isMenuOpen = ref(false)

const navItems = [
  'Bahçe Kapısı',
  'Garaj Kapısı',
  'Fotoselli Kapı',
  'Endüstriyel Kapı',
  'Yangın Dayanımlı Kapı'
]

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}
</script>

<template>
  <header class="header">
    <nav class="nav">
      <div class="nav-left">
        <a href="#" class="brand">Kapı Portal</a>
      </div>

      <div class="nav-center" :class="{ 'nav-center-open': isMenuOpen }">
        <a v-for="item in navItems" :key="item" href="#" class="nav-link">
          {{ item }}
        </a>
      </div>

      <div class="nav-right">
        <a href="#" class="nav-icon" aria-label="Profil">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
            <circle cx="12" cy="8" r="4"/>
            <path d="M4 20c0-4 3.5-7 8-7s8 3 8 7"/>
          </svg>
        </a>
        <a href="#" class="nav-icon" aria-label="İletişim">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
            <path d="M21 15a2 2 0 01-2 2H7l-4 4V5a2 2 0 012-2h14a2 2 0 012 2z"/>
          </svg>
        </a>
        <button class="menu-toggle" @click="toggleMenu" aria-label="Menü">
          <svg v-if="!isMenuOpen" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
            <line x1="3" y1="6" x2="21" y2="6"/>
            <line x1="3" y1="12" x2="21" y2="12"/>
            <line x1="3" y1="18" x2="21" y2="18"/>
          </svg>
          <svg v-else width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
            <line x1="18" y1="6" x2="6" y2="18"/>
            <line x1="6" y1="6" x2="18" y2="18"/>
          </svg>
        </button>
      </div>
    </nav>
  </header>

  <main>
    <h1>Merhaba Tolga</h1>
  </main>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: #000;
  color: #fff;
}

.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  background: rgba(0, 0, 0, 0.8);
  backdrop-filter: saturate(180%) blur(20px);
  -webkit-backdrop-filter: saturate(180%) blur(20px);
}

.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  max-width: 980px;
  margin: 0 auto;
  height: 44px;
  padding: 0 22px;
}

.nav-left {
  flex-shrink: 0;
}

.brand {
  color: #f5f5f7;
  text-decoration: none;
  font-size: 14px;
  font-weight: 500;
  opacity: 0.9;
  transition: opacity 0.3s;
}

.brand:hover {
  opacity: 1;
}

.nav-center {
  display: flex;
  gap: 32px;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
}

.nav-link {
  color: #f5f5f7;
  text-decoration: none;
  font-size: 12px;
  font-weight: 400;
  opacity: 0.8;
  transition: opacity 0.3s;
  white-space: nowrap;
}

.nav-link:hover {
  opacity: 1;
}

.nav-right {
  display: flex;
  align-items: center;
  gap: 16px;
  flex-shrink: 0;
}

.nav-icon {
  color: #f5f5f7;
  text-decoration: none;
  opacity: 0.8;
  transition: opacity 0.3s;
  display: flex;
  align-items: center;
}

.nav-icon:hover {
  opacity: 1;
}

.menu-toggle {
  display: none;
  background: none;
  border: none;
  color: #f5f5f7;
  cursor: pointer;
  padding: 4px;
}

main {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  padding-top: 44px;
}

h1 {
  font-size: 2rem;
  font-weight: 500;
  color: #f5f5f7;
}

/* Mobile styles */
@media (max-width: 768px) {
  .nav-center {
    display: none;
    position: fixed;
    top: 44px;
    left: 0;
    right: 0;
    background: rgba(0, 0, 0, 0.95);
    backdrop-filter: blur(20px);
    flex-direction: column;
    padding: 20px;
    gap: 20px;
  }

  .nav-center.nav-center-open {
    display: flex;
  }

  .nav-link {
    font-size: 14px;
  }

  .menu-toggle {
    display: flex;
  }

  h1 {
    font-size: 1.5rem;
  }
}
</style>