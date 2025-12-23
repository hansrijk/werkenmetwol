<script setup>
</script>

<template>
  <section class="section about">
    <div class="container">
      <h2>Over Mij</h2>
      <div class="about-content">
        <div class="about-text">
          <p>
            Welkom! Ik ben gek op alles wat met wol te maken heeft. Al meer dan 10 jaar geleden begon mijn liefde voor vilten,
            en sindsdien heb ik talloze workshops gegeven en veel prachtige producten gemaakt.
          </p>
          <p>
            Mijn passie is om anderen te inspireren en de kunst van vilten over te brengen. Door het creatieve proces met wol 
            kunnen mensen tot rust komen en iets moois creëren. Elk product dat uit mijn atelier komt, is met veel liefde en 
            aandacht gemaakt.
          </p>
        </div>
        <div class="about-image">
          <div class="image-placeholder">
            <svg viewBox="0 0 300 300" xmlns="http://www.w3.org/2000/svg">
              <!-- Achtergrond -->
              <rect width="300" height="300" fill="#f0f0f0" rx="15"/>
              
              <!-- Persoon silhouet -->
              <circle cx="150" cy="80" r="35" fill="#667eea" opacity="0.8"/>
              <path d="M 100 130 Q 100 115, 150 115 Q 200 115, 200 130 L 200 200 Q 200 220, 150 220 Q 100 220, 100 200 Z" 
                    fill="#764ba2" opacity="0.8"/>
              
              <!-- Decoratieve wol elementen -->
              <circle cx="60" cy="100" r="20" fill="#e8b4e8" opacity="0.6"/>
              <circle cx="240" cy="120" r="25" fill="#d4a5d4" opacity="0.6"/>
              <circle cx="80" cy="180" r="18" fill="#c8a2d8" opacity="0.5"/>
              <circle cx="220" cy="200" r="22" fill="#d9b3e0" opacity="0.5"/>
              
              <!-- Decoratieve lijnen -->
              <path d="M 50 150 Q 100 140, 150 150" stroke="#667eea" stroke-width="2" fill="none" opacity="0.4"/>
              <path d="M 150 150 Q 200 160, 250 150" stroke="#764ba2" stroke-width="2" fill="none" opacity="0.4"/>
            </svg>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.section {
  background: white;
  margin: 40px 30px;
  border-radius: 20px;
  padding: 60px 30px;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.15);
}

.container {
  max-width: 1000px;
  margin: 0 auto;
}

.section h2 {
  color: #667eea;
  font-size: 2.5em;
  text-align: center;
  margin-bottom: 40px;
}

.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  align-items: center;
}

.about-text {
  color: #555;
  line-height: 1.8;
}

.about-text p {
  margin-bottom: 20px;
  text-align: justify;
  font-size: 1em;
}

.about-text p:last-child {
  margin-bottom: 0;
}

.about-image {
  display: flex;
  justify-content: center;
  align-items: center;
}

.image-placeholder {
  width: 100%;
  max-width: 300px;
  aspect-ratio: 1;
  background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
}

.image-placeholder svg {
  width: 100%;
  height: 100%;
}

@media (max-width: 768px) {
  .about-content {
    grid-template-columns: 1fr;
    gap: 30px;
  }

  .about-text p {
    text-align: left;
  }

  .section {
    margin: 20px 15px;
    padding: 40px 20px;
  }

  .section h2 {
    font-size: 2em;
  }
}
</style>
