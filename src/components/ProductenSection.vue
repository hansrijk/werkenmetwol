<script setup>
import 'vue3-carousel/carousel.css'
import { Carousel, Slide, Navigation } from 'vue3-carousel'
import { ref, onMounted, onUnmounted } from 'vue'

const currentSlide = ref(0)
const isFullscreen = ref(false)

const slideTo = (nextSlide) => (currentSlide.value = nextSlide)

const openFullscreen = () => {
  isFullscreen.value = true
  document.body.style.overflow = 'hidden'
}

const closeFullscreen = () => {
  isFullscreen.value = false
  document.body.style.overflow = ''
}

const onKeydown = (e) => {
  if (e.key === 'Escape' && isFullscreen.value) {
    closeFullscreen()
  }
}

onMounted(() => window.addEventListener('keydown', onKeydown))
onUnmounted(() => window.removeEventListener('keydown', onKeydown))

const galleryConfig = {
  itemsToShow: 1,
  wrapAround: true,
  slideEffect: 'fade',
  mouseDrag: false,
  touchDrag: false,
  height: 400,
}

const thumbnailsConfig = {
  height: 100,
  itemsToShow: 6,
  wrapAround: true,
  touchDrag: false,
  gap: 10,
}

const images = [
  '1.png',
  '12b.jpg',
  '14a.jpg',
  '16d.jpg',
  '17a.jpg',
  '1a.jpg',
  '2a.jpg',
  'foto (1).png',
  'foto (10).png',
  'foto (11).png',
  'foto (12).png',
  'foto (2).png',
  'foto (3).png',
  'foto (4).png',
  'foto (5).png',
  'foto (6).png',
  'foto (7).png',
  'foto (8).png',
  'foto (9).png',
].map((name, index) => ({
  id: index + 1,
  url: `/producten/${name}`,
}))

</script>

<template>
  <section class="section producten">
    <div class="container">
      <h2>Producten</h2>
      <div class="carousel-wrapper">
        <Carousel id="gallery" v-bind="galleryConfig" v-model="currentSlide">
          <Slide v-for="image in images" :key="image.id">
            <img :src="image.url" alt="Gallery Image" class="gallery-image" @click="openFullscreen" />
          </Slide>

          <template #addons>
            <Navigation />
          </template>
        </Carousel>

        <Carousel id="thumbnails" v-bind="thumbnailsConfig" v-model="currentSlide">
          <Slide v-for="image in images" :key="image.id">
            <template #default="{ currentIndex, isActive }">
              <div
                :class="['thumbnail', { 'is-active': isActive }]"
                @click="slideTo(currentIndex)"
              >
                <img :src="image.url" alt="Thumbnail Image" class="thumbnail-image" />
              </div>
            </template>
          </Slide>
        </Carousel>
      </div>

      <!-- Fullscreen overlay -->
      <div v-if="isFullscreen" class="fullscreen-overlay" @click.self="closeFullscreen">
        <button class="fullscreen-close" @click="closeFullscreen">&times;</button>
        <div class="fullscreen-carousel">
          <Carousel id="fullscreen-gallery" :items-to-show="1" :wrap-around="true" v-model="currentSlide">
            <Slide v-for="image in images" :key="image.id">
              <img :src="image.url" alt="Gallery Image" class="fullscreen-image" />
            </Slide>
            <template #addons>
              <Navigation />
            </template>
          </Carousel>

          <Carousel id="fullscreen-thumbnails" :height="80" :items-to-show="8" :wrap-around="true" :gap="10" v-model="currentSlide">
            <Slide v-for="image in images" :key="image.id">
              <template #default="{ currentIndex, isActive }">
                <div
                  :class="['thumbnail', { 'is-active': isActive }]"
                  @click="slideTo(currentIndex)"
                >
                  <img :src="image.url" alt="Thumbnail" class="thumbnail-image" />
                </div>
              </template>
            </Slide>
          </Carousel>
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

.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 30px;
}

.product-card {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  border-radius: 15px;
  padding: 30px;
  text-align: center;
  transition: all 0.3s;
}

.product-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 30px rgba(102, 126, 234, 0.4);
}

.product-image {
  font-size: 4em;
  margin-bottom: 15px;
}

.product-card h3 {
  color: white;
  font-size: 1.4em;
  margin-bottom: 10px;
}

.product-card p {
  color: white;
}

/* Carousel */
.carousel-wrapper {
  margin-top: 50px;
}

.carousel {
  --vc-nav-background: rgba(255, 255, 255, 0.7);
  --vc-nav-border-radius: 100%;
  --vc-nav-width: 40px;
  --vc-nav-height: 40px;
  --vc-nav-color: #333;
}

:deep(.carousel__prev) {
  left: 20px;
}

:deep(.carousel__next) {
  right: 20px;
}

img {
  border-radius: 8px;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.gallery-image {
  border-radius: 16px;
  cursor: pointer;
  object-fit: contain;
  background: #f0f0f0;
}

#thumbnails {
  margin-top: 10px;
}

.thumbnail {
  height: 100%;
  width: 100%;
  cursor: pointer;
  opacity: 0.6;
  transition: opacity 0.3s ease-in-out;
}

.thumbnail.is-active,
.thumbnail:hover {
  opacity: 1;
}

/* Fullscreen */
.fullscreen-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.92);
  z-index: 1000;
  display: flex;
  align-items: center;
  justify-content: center;
}

.fullscreen-close {
  position: absolute;
  top: 20px;
  right: 30px;
  background: none;
  border: none;
  color: white;
  font-size: 3em;
  cursor: pointer;
  z-index: 1001;
  line-height: 1;
}

.fullscreen-close:hover {
  color: #ccc;
}

.fullscreen-carousel {
  width: 90vw;
  max-width: 1200px;
}

.fullscreen-image {
  width: 100%;
  max-height: 75vh;
  object-fit: contain;
  border-radius: 8px;
}

#fullscreen-thumbnails {
  margin-top: 15px;
}

@media (max-width: 768px) {
  .section {
    margin: 20px 15px;
    padding: 40px 20px;
  }
}
</style>
