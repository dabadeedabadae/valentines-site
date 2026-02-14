<template>
  <div class="container">
    <FloatingHearts />

    <div class="love-card">
      <h1>I love you ❤️</h1>

      <div class="images">
        <img src="/cat.gif" class="cat" />
        <img src="/coffee.png" class="coffee" />
      </div>

      <p class="text">
        You + Me + Coffee + Cats = Perfect Valentine ☕🐱💞
      </p>
    </div>
  </div>
</template>

<script setup>
import FloatingHearts from '~/components/FloatingHearts.vue'
</script>

<style scoped>
.container {
  height: 100vh;
  width: 100vw;
  background: linear-gradient(135deg, #ff2f6d, #ff9bb3);
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  position: relative;
}

.love-card {
  background: white;
  padding: 50px;
  border-radius: 20px;
  text-align: center;
  box-shadow: 0 20px 50px rgba(0,0,0,0.3);
  z-index: 2;
}

.images {
  display: flex;
  justify-content: center;
  gap: 30px;
  margin: 20px 0;
}

.cat {
  width: 180px;
}

.coffee {
  width: 120px;
}
</style>
