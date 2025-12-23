<script setup>
const products = [
  { 
    icon: '🐑', 
    title: 'Schapenvachten', 
    description: 'Gevilte en natuurlijke vachten' 
  },
  { 
    icon: '🧶', 
    title: 'Art yarns', 
    description: 'Geverfde en unieke art yarns' 
  },
  { 
    icon: '🎁', 
    title: 'Nog meer producten', 
    description: 'Nog veel meer, zoals poppen en sieraden' 
  }
]
</script>

<template>
  <section class="section producten">
    <div class="container">
      <h2>Handgemaakte Producten</h2>
      <p class="section-intro">Unieke producten van wol en vilt; met liefde gemaakt</p>
      
      <div class="product-grid">
        <div v-for="product in products" :key="product.title" class="product-card">
          <div class="product-image">{{ product.icon }}</div>
          <h3>{{ product.title }}</h3>
          <p>{{ product.description }}</p>
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
  margin-bottom: 15px;
}

.section-intro {
  text-align: center;
  color: #666;
  font-size: 1.1em;
  margin-bottom: 50px;
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

@media (max-width: 768px) {
  .section {
    margin: 20px 15px;
    padding: 40px 20px;
  }
}
</style>
