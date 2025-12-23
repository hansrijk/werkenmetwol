<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import HeroSection from './components/HeroSection.vue'
import ProductenSection from './components/ProductenSection.vue'
import AboutSection from './components/AboutSection.vue'
import ContactSection from './components/ContactSection.vue'

const activeSection = ref('home')

const menuItems = [
  { id: 'home', label: 'Home' },
  { id: 'producten', label: 'Producten' },
  { id: 'over', label: 'Over Mij' },
  { id: 'contact', label: 'Contact' }
]

const scrollToSection = (sectionId) => {
  activeSection.value = sectionId
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
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
        <div class="logo">
          <div class="logo-icon">
            <svg viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
              <!-- Wol bal -->
              <circle cx="50" cy="50" r="35" fill="white" opacity="0.9"/>
              <path d="M 30 40 Q 40 35, 50 40 T 70 40" stroke="white" stroke-width="3" fill="none" opacity="0.7"/>
              <path d="M 30 50 Q 40 45, 50 50 T 70 50" stroke="white" stroke-width="3" fill="none" opacity="0.7"/>
              <path d="M 30 60 Q 40 55, 50 60 T 70 60" stroke="white" stroke-width="3" fill="none" opacity="0.7"/>
            </svg>
          </div>
          <div class="logo-text">
            <h1>Werken met Wol</h1>
            <p>Vilten & Wolproducten</p>
          </div>
        </div>
        
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

    <!-- Hero Section -->
    <HeroSection :id="'home'" />

    <!-- Producten Section -->
    <ProductenSection :id="'producten'" />

    <!-- About Section -->
    <AboutSection :id="'over'" />

    <!-- Contact Section -->
    <ContactSection :id="'contact'" />

    <!-- Footer -->
    <footer class="footer">
      <p>&copy; 2025 Werken met Wol - Alle rechten voorbehouden</p>
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
  background: rgba(255, 255, 255, 0.95);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  position: sticky;
  top: 0;
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
