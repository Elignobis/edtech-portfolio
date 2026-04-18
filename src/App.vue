<template>
  <div :class="{ dark: isDark }">
    <nav class="navbar">
      <span class="logo">Ta Sbo | EdTechie</span>
      <div style="display: flex; align-items: center; gap: 1.5rem;">
        <button class="dark-toggle" @click="toggleDark" :title="isDark ? 'Light mode' : 'Dark mode'">
          {{ isDark ? '☀️' : '🌙' }}
        </button>
        <button class="hamburger" @click="menuOpen = !menuOpen">
          <span></span>
          <span></span>
          <span></span>
        </button>
      </div>
      <div class="nav-links" :class="{ open: menuOpen }">
        <a href="#about" @click="menuOpen = false">About</a>
        <a href="#projects" @click="menuOpen = false">Projects</a>
        <a href="#skills" @click="menuOpen = false">Skills</a>
        <a href="#contact" @click="menuOpen = false">Contact</a>
      </div>
    </nav>
    <RouterView />
  </div>
  <!-- Back to top button -->
<button class="back-to-top" :class="{ visible: showTop }" @click="scrollToTop">
  ↑
</button>
</template>

<script setup>
import { ref } from 'vue'

const isDark = ref(false)
const menuOpen = ref(false)

function toggleDark() {
  isDark.value = !isDark.value
  localStorage.setItem('darkMode', isDark.value)
}

// Remember user's preference
const saved = localStorage.getItem('darkMode')
if (saved === 'true') isDark.value = true

import {  onMounted, onUnmounted } from 'vue'

const showTop = ref(false)

function handleScroll() {
  showTop.value = window.scrollY > 400
}

function scrollToTop() {
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style>
/* Light mode variables */
:root {
  --bg: #f8fafc;
  --bg-alt: #f1f5f9;
  --surface: #ffffff;
  --text: #1e293b;
  --text-muted: #64748b;
  --primary: #2563eb;
  --primary-hover: #1d4ed8;
  --shadow: rgba(0,0,0,0.08);
  --border: #e2e8f0;
}

/* Dark mode variables */
.dark {
  --bg: #0f172a;
  --bg-alt: #1e293b;
  --surface: #1e293b;
  --text: #f1f5f9;
  --text-muted: #94a3b8;
  --primary: #3b82f6;
  --primary-hover: #2563eb;
  --shadow: rgba(0,0,0,0.3);
  --border: #334155;
}

*, *::before, *::after { box-sizing: border-box; }

html, body {
  margin: 0;
  padding: 0;
  width: 100%;
  min-height: 100vh;
}

#app { width: 100%; }

body {
  font-family: 'Outfit', sans-serif;
}

/* Apply theme to the wrapper div */
#app > div {
  background: var(--bg);
  color: var(--text);
  min-height: 100vh;
  transition: background 0.3s, color 0.3s;
}

/* Navbar */
.navbar {
  background: var(--surface);
  padding: 1rem 3rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 2px 10px var(--shadow);
  position: sticky;
  top: 0;
  z-index: 100;
  width: 100%;
  transition: background 0.3s;
  border-bottom: 1px solid var(--border);
}

.logo {
  font-weight: 700;
  font-size: 1.2rem;
  color: var(--primary);
}

.nav-links {
  display: flex;
  gap: 2rem;
}

.nav-links a {
  text-decoration: none;
  color: var(--text);
  font-weight: 500;
  font-size: 0.95rem;
  transition: color 0.2s;
}

.nav-links a:hover { color: var(--primary); }

/* Dark mode toggle button */
.dark-toggle {
  background: var(--bg-alt);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 0.4rem 0.6rem;
  cursor: pointer;
  font-size: 1.1rem;
  transition: background 0.2s;
  line-height: 1;
}

.dark-toggle:hover { background: var(--border); }

/* Hamburger */
.hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 4px;
}

.hamburger span {
  display: block;
  width: 24px;
  height: 2px;
  background: var(--text);
  border-radius: 2px;
  transition: all 0.3s;
}

/* Mobile */
@media (max-width: 640px) {
  .navbar {
    padding: 1rem 1.5rem;
    flex-wrap: wrap;
  }

  .hamburger { display: flex; }

  .nav-links {
    display: none;
    flex-direction: column;
    gap: 0;
    width: 100%;
    padding: 0.5rem 0 1rem;
  }

  .nav-links.open { display: flex; }

  .nav-links a {
    padding: 0.75rem 0;
    border-bottom: 1px solid var(--border);
    font-size: 1rem;
  }
}
/* Back to top button */
.back-to-top {
  position: fixed;
  bottom: 2rem;
  right: 2rem;
  width: 48px;
  height: 48px;
  border-radius: 12px;
  background: linear-gradient(135deg, #1e40af, #3b82f6);
  color: white;
  border: none;
  font-size: 1.3rem;
  cursor: pointer;
  box-shadow: 0 8px 25px rgba(37, 99, 235, 0.4);
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.3s, transform 0.3s, box-shadow 0.3s;
  z-index: 999;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
}

.back-to-top.visible {
  opacity: 1;
  transform: translateY(0);
}

.back-to-top:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 35px rgba(37, 99, 235, 0.5);
}

.back-to-top:active {
  transform: translateY(-1px);
}
</style>