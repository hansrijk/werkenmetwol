<script setup>
const scrollToContact = () => {
  const contactSection = document.getElementById('contact')
  if (contactSection) {
    contactSection.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<template>
  <section class="hero" id="home">
    <div class="hero-content">
      <h2>Viltatelier Werken met Wol</h2>
      <p>Hoi. Welkom op de website van mijn viltatelier, waar je mijn handgemaakte wolproducten kunt ontdekken. Laat het gerust weten als je vragen of opmerkingen hebt!</p>
      <button class="btn-primary" @click="scrollToContact">Contact opnemen</button>
    </div>
    <div class="hero-image">
      <div class="sheep-placeholder">
        <svg viewBox="0 0 200 150" xmlns="http://www.w3.org/2000/svg">
          <!-- Schaap 1 -->
          <ellipse cx="60" cy="80" rx="35" ry="30" fill="white" opacity="0.9"/>
          <circle cx="45" cy="75" r="8" fill="white" opacity="0.9"/>
          <circle cx="75" cy="75" r="8" fill="white" opacity="0.9"/>
          <ellipse cx="80" cy="70" rx="15" ry="12" fill="#f0f0f0"/>
          <circle cx="78" cy="68" r="3" fill="#333"/>
          <circle cx="86" cy="68" r="3" fill="#333"/>
          
          <!-- Schaap 2 -->
          <ellipse cx="140" cy="90" rx="32" ry="28" fill="white" opacity="0.85"/>
          <circle cx="125" cy="85" r="7" fill="white" opacity="0.85"/>
          <circle cx="155" cy="85" r="7" fill="white" opacity="0.85"/>
          <ellipse cx="160" cy="80" rx="14" ry="11" fill="#f0f0f0"/>
          <circle cx="158" cy="78" r="2.5" fill="#333"/>
          <circle cx="165" cy="78" r="2.5" fill="#333"/>
          
          <!-- Gras -->
          <path d="M 0 120 Q 50 115, 100 120 T 200 120 L 200 150 L 0 150 Z" fill="#98d8c8" opacity="0.6"/>
        </svg>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  max-width: 1200px;
  margin: 0 auto;
  padding: 60px 30px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  align-items: center;
}

.hero-content h2 {
  color: white;
  font-size: 3em;
  margin-bottom: 20px;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
}

.hero-content p {
  color: white;
  font-size: 1.3em;
  margin-bottom: 30px;
  opacity: 0.95;
}

.btn-primary {
  background: white;
  color: #667eea;
  border: none;
  padding: 15px 40px;
  font-size: 1.1em;
  font-weight: 600;
  border-radius: 30px;
  cursor: pointer;
  transition: all 0.3s;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
}

.btn-primary:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
}

.hero-image {
  display: flex;
  justify-content: center;
  align-items: center;
}

.sheep-placeholder {
  width: 100%;
  max-width: 400px;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 20px;
  padding: 30px;
  backdrop-filter: blur(10px);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
}

.sheep-placeholder svg {
  width: 100%;
  height: auto;
}

@media (max-width: 768px) {
  .hero {
    grid-template-columns: 1fr;
    text-align: center;
  }
  
  .hero-content h2 {
    font-size: 2em;
  }
}
</style>
