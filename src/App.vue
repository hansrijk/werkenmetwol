<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import HeroSection from './components/HeroSection.vue'
import AgendaSection from './components/AgendaSection.vue'
import ProductenSection from './components/ProductenSection.vue'
import AboutSection from './components/AboutSection.vue'
import ContactSection from './components/ContactSection.vue'

const activeSection = ref('home')

const menuItems = [
  { id: 'home', label: 'Home' },
  { id: 'agenda', label: 'Agenda' },
  { id: 'producten', label: 'Producten' },
  { id: 'over', label: 'Over Mij' },
  { id: 'contact', label: 'Contact' }
]

const scrollToSection = (sectionId) => {
  activeSection.value = sectionId
  const element = document.getElementById(sectionId)
  if (element) {
    const headerHeight = document.querySelector('.header')?.offsetHeight || 120
    const elementPosition = element.getBoundingClientRect().top + window.scrollY
    window.scrollTo({ top: elementPosition - headerHeight, behavior: 'smooth' })
  }
}

const updateActiveSection = () => {
  const sections = menuItems.map(item => item.id)
  for (const sectionId of sections) {
    const element = document.getElementById(sectionId)
    if (element) {
      const rect = element.getBoundingClientRect()
      if (rect.top <= window.innerHeight / 2) {
        activeSection.value = sectionId
      }
    }
  }
}

onMounted(() => {
  window.addEventListener('scroll', updateActiveSection)
})

onUnmounted(() => {
  window.removeEventListener('scroll', updateActiveSection)
})
</script>

<template>
  <div class="app">
    <!-- Header met Logo en Menu -->
    <header class="header">
      <div class="header-content">
        <a href="/" style="text-decoration:none">
        <div class="logo">
          <div class="logo-icon" style="padding-right: 50px;">
            <img src="/public/favicon.ico" height="100px" alt="logo">
          </div>
          <div class="logo-text">
            <h1>Werken Met Wol</h1>
            <p>Viltatelier in Biddinghuizen</p>
          </div>
        </div>
        </a>
        
        <nav class="nav">
          <a 
            v-for="item in menuItems" 
            :key="item.id"
            @click="scrollToSection(item.id)"
            :class="{ active: activeSection === item.id }"
          >
            {{ item.label }}
          </a>
        </nav>
      </div>
    </header>

    <!-- Spacer for fixed header -->
    <div class="header-spacer"></div>

    <!-- Hero Section -->
    <HeroSection :id="'home'" />

    <!-- Agenda Section -->
    <AgendaSection :id="'agenda'" />

    <!-- Producten Section -->
    <ProductenSection :id="'producten'" />

    <!-- About Section -->
    <AboutSection :id="'over'" />

    <!-- Contact Section -->
    <ContactSection :id="'contact'" />

    <!-- Footer -->
    <footer class="footer">
      <p>&copy; 2026 - Werken met Wol - Alle rechten voorbehouden</p>
    </footer>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  min-height: 100vh;
}

/* Header */
.header {
  background: rgba(255, 255, 255, 1);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 100;
}

.header-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px 30px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 20px;
}

.logo {
  display: flex;
  align-items: center;
  gap: 15px;
}

.logo-icon {
  width: 60px;
  height: 60px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px;
}

.logo-icon svg {
  width: 100%;
  height: 100%;
}

.logo-text h1 {
  color: #667eea;
  font-size: 1.8em;
  font-weight: 700;
  line-height: 1;
  margin-bottom: 5px;
}

.logo-text p {
  color: #764ba2;
  font-size: 0.9em;
  font-style: italic;
}

.nav {
  display: flex;
  gap: 30px;
}

.nav a {
  color: #555;
  text-decoration: none;
  font-weight: 600;
  font-size: 1em;
  padding: 8px 16px;
  border-radius: 8px;
  transition: all 0.3s;
  cursor: pointer;
}

.nav a:hover {
  color: #667eea;
  background: rgba(102, 126, 234, 0.1);
}

.nav a.active {
  color: white;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.header-spacer {
  height: 120px;
}

/* Footer */
.footer {
  background: rgba(255, 255, 255, 0.95);
  text-align: center;
  padding: 10px;
  color: #666;
  margin-top: 40px;
}

/* Responsive */
@media (max-width: 768px) {
  .header-content {
    flex-direction: column;
    text-align: center;
  }
  
  .nav {
    flex-wrap: wrap;
    justify-content: center;
    gap: 10px;
  }
}
</style>
