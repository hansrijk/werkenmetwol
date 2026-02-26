<script setup>
const contactInfo = [
  { icon: '<i class="fa-solid fa-envelope" style="font-size:24px"></i>', text: 'werkenmetwol@planet.nl', link: 'mailto:werkenmetwol@planet.nl' },
  { icon: '<i class="fa-solid fa-phone" style="font-size:24px"></i>', text: '0612685399', link: 'tel:0612685399' },
  { icon: '<i class="fa-brands fa-facebook-f" style="font-size:24px"></i>', text: 'Facebook', link: 'https://www.facebook.com/werkenmetwol/' },
  { icon: '<i class="fa-brands fa-instagram" style="font-size:24px"></i>', text: 'Instagram', link: 'https://www.instagram.com/werkenmetwol/' },
  { icon: '<i class="fa-solid fa-location-dot" style="font-size:24px"></i>', text: 'Harderringweg 6, 8256 PT Biddinghuizen', link: null }
]
</script>

<template>
  <section class="section contact">
    <div class="container">
      <h2>Contact</h2>
      <p class="section-intro">Vragen? Neem gerust contact op</p>
      
      <div class="contact-info">
        <div v-for="(item, index) in contactInfo" :key="index" class="contact-item">
          <span class="icon" v-html="item.icon"></span>
          <a v-if="item.link" :href="item.link" class="contact-link">{{ item.text }}</a>
          <span v-else>{{ item.text }}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.section {
  background: white;
  margin: 40px 0;
  border-radius: 0;
  padding: 60px 30px;
  box-shadow: none;
}

.contact {
  background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);
}

.container {
  max-width: 1000px;
  margin: 0 auto;
}

.section h2 {
  color: #667eea;
  font-size: 2.5em;
  text-align: center;
  margin-bottom: 20px;
}

.section-intro {
  text-align: center;
  color: #666;
  font-size: 1.1em;
  margin-bottom: 50px;
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 20px;
  max-width: 500px;
  margin: 0 auto;
}

.contact-item {
  display: flex;
  align-items: center;
  gap: 15px;
  background: white;
  padding: 20px;
  border-radius: 12px;
  font-size: 1.1em;
  color: #555;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.contact-item .icon {
  font-size: 1.8em;
}

@media (max-width: 768px) {
  .section {
    margin: 20px 15px;
    padding: 40px 20px;
  }

  .section h2 {
    font-size: 1.5em;
  }

  .section-intro {
    font-size: 0.95em;
    margin-bottom: 30px;
  }

  .contact-item {
    padding: 14px;
    font-size: 0.95em;
  }
}
</style>
