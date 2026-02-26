<script setup>
import { computed } from 'vue'

// voeg hier de datums toe voor dit jaar. Maanden die al geweest zijn, worden niet getoond
const dates = [
  { date: 'Zaterdag 3 januari', month: 0 },
  { date: 'Zaterdag 7 febuari', month: 1 },
  { date: 'Zaterdag 7 maart', month: 2 },
  { date: 'Zaterdag 4 april', month: 3 },
  { date: 'Zaterdag 2 mei', month: 4 },
  { date: 'Zaterdag 6 juni', month: 5 },
  { date: 'Zaterdag 20 juni (Zomermarkt)', month: 5 },
  { date: 'Zaterdag 4 juli', month: 6 },
  { date: 'Zaterdag 1 augustus', month: 7 },
  { date: 'Zaterdag 5 september', month: 8 },
  { date: 'Zaterdag 19 september (Oogstfeest)', month: 8 },
  { date: 'Zaterdag 3 oktober', month: 9 },
  { date: 'Zaterdag 7 november', month: 10 },
  { date: 'Zaterdag 5 december', month: 11 },
  { date: 'Zaterdag 19 december (Kerstmarkt)', month: 11 },
]

const upcomingDates = computed(() => {
  const currentMonth = new Date().getMonth()
  return dates.filter(d => d.month >= currentMonth)
})
</script>

<template>
  <section class="section about">
    <div class="container">
      <h2>Agenda</h2>
      <div class="about-content">
        <div class="about-text">
          <p>
            Op onderstaande data ben ik te vinden op de biologische boerenmarkt in Almere. <br> Het adres is <a href="https://www.google.com/maps/place/De+Stadsboerderij/@52.3425094,5.2706717,458m/data=!3m2!1e3!4b1!4m6!3m5!1s0x47c616119d56115d:0xb146a2d759c1765a!8m2!3d52.3425094!4d5.2706717!16s%2Fg%2F11h0jg_rl?entry=ttu&g_ep=EgoyMDI2MDIxOC4wIKXMDSoASAFQAw%3D%3D">Kemphaanpad 14, 1358 AC Almere</a>. Meer info op <a href="https://stadsboerderijalmere.nl/erf-kemphaanpad/boerenmarkt">de website van de stadsboederij</a>
          </p>
          <p>
            <span v-for="(item, index) in upcomingDates" :key="index">
              {{ item.date }}<br>
            </span>
          </p>
        </div>
        <div class="about-image">
          <div class="image-placeholder">
            <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d1993.1959263521728!2d5.2706717!3d52.342509400000004!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x47c616119d56115d%3A0xb146a2d759c1765a!2sDe%20Stadsboerderij!5e1!3m2!1snl!2snl!4v1771957781672!5m2!1snl!2snl" width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
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
  margin-bottom: 20px;
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
  max-width: 400px;
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
