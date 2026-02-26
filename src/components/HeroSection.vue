<script setup>
const scrollToContact = () => {
  const contactSection = document.getElementById('contact')
  if (contactSection) {
    const headerHeight = document.querySelector('.header')?.offsetHeight || 120
    const pos = contactSection.getBoundingClientRect().top + window.scrollY
    window.scrollTo({ top: pos - headerHeight, behavior: 'smooth' })
  }
}

const scrollToAgenda = (e) => {
  e.preventDefault()
  const agendaSection = document.getElementById('agenda')
  if (agendaSection) {
    const headerHeight = document.querySelector('.header')?.offsetHeight || 120
    const pos = agendaSection.getBoundingClientRect().top + window.scrollY
    window.scrollTo({ top: pos - headerHeight, behavior: 'smooth' })
  }
}
</script>

<template>
  <section class="hero" id="home">
    <div class="hero-content">
      <h2>Werken Met Wol</h2>
      <h3>Viltatelier in Biddinghuizen</h3>
      <br>
      <p>Je bent bij mij op het goede adres om mooie en duurzame producten van wol te kopen. Iedere eerste zaterdag van de maand sta ik met mijn wol producten op de biologische markt op stadsboederij De Kemphaan in Almere. 
        Klik <a href="#agenda" @click="scrollToAgenda">hier</a>  om naar de agenda te gaan
      </p>
      <button class="btn-primary" @click="scrollToContact">Contact opnemen</button>
    </div>
    <div class="hero-image">
      <div class="homepage-foto">
        <img src="/public/homepage.jpg" alt="homepage foto">
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  max-width: 1200px;
  margin: 20px auto;
  padding: 60px 30px;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  align-items: center;
}

.hero-content h2 {
  color: white;
  font-size: 4em;
  margin-bottom: 20px;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
}

.hero-content h3 {
  color: white;
  font-size: 2em;
  margin-bottom: 20px;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
}

.hero-content p {
  color: white;
  font-size: 1.4em;
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

.homepage-foto {
  width: 100%;
  max-width: 500px;
  border-radius: 5%;
  padding: 30px;
  backdrop-filter: blur(10px);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.6);
}

.homepage-foto img {
  width: 100%;
  height: auto;
}

@media (max-width: 1024px) {
  .hero {
    grid-template-columns: 1fr;
    text-align: center;
    padding: 40px 20px;
    gap: 30px;
  }

  .hero-content h2 {
    font-size: 2.5em;
  }

  .hero-content h3 {
    font-size: 1.4em;
  }

  .hero-content p {
    font-size: 1.1em;
  }

  .homepage-foto {
    max-width: 400px;
    margin: 0 auto;
  }
}

@media (max-width: 768px) {
  .hero {
    padding: 30px 16px;
    gap: 24px;
  }

  .hero-content h2 {
    font-size: 1.6em;
  }

  .hero-content h3 {
    font-size: 1.1em;
  }

  .hero-content p {
    font-size: 1em;
  }

  .btn-primary {
    padding: 12px 30px;
    font-size: 0.95em;
  }

  .homepage-foto {
    padding: 15px;
  }
}
</style>
