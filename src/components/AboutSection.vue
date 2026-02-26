<script setup>
</script>

<template>
  <section class="section about">
    <div class="container">
      <h2>Over Mij</h2>
      <div class="about-content">
        <div class="about-image">
          <div class="over-mij-foto">
            <img src="/public/over_mij.jpg" alt="over mij foto">
          </div>
        </div>

        <div class="about-text">
          <p>
            Sinds ik, in ongeveer 2001, mijn eigen atelier ben gestart heb ik veel workshops mogen geven waarin mensen mooie producten hebben gemaakt. 
            <br><br>
            Sinds januari 2025 ben ik gestopt met het geven van workshops. 
            Hierdoor heb ik meer tijd om producten te maken die ik verkoop op de markt in Almere, op fairs en tijdens evenementen elders in het land.
            <br><br>
            Je kan wandkleden van mij zien en kopen in het lunch cafe gedeelte van de Odin winkel in Almere Oosterwold. 
            Zie <a href="https://www.odin.nl/over-odin/winkels/-62659-odin-almere-vliervelden/">de website van Odin</a> voor meer informatie.
            <br><br>
            Ook kun je mij vinden op <a href="https://www.facebook.com/werkenmetwol">Facebook</a> en <a href="https://www.instagram.com/werkenmetwol">Instagram</a>           
          </p>
        </div>
        
      </div>
    </div>
  </section>
</template>

<style scoped>
.section {
  background: white;
  margin: 20px 30px 10px;
  border-radius: 20px;
  padding: 60px 30px; 
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.15);
}

.container {
  max-width: 1200px;
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
  align-items: start;
}

.about-text {
  margin-top: 5px;
  color: #555;
  line-height: 1.8;
}

.about-text p {
  margin-bottom: 0x;
  text-align: justify;
  font-size: 1.1em;
}

.about-text p:last-child {
  margin-bottom: 0;
}

.about-image {
  display: flex;
  justify-content: center;
  align-items: center;
}

.over-mij-foto {
  width: 100%;
  max-width: 800px;
}

.over-mij-foto img {
  width: 100%;
  border-radius:5%;
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
