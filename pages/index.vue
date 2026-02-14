<template>
  <div class="container">
    <FloatingHearts />

    <div class="card">
      <h1>Will you be my Valentine? 💖</h1>

      <div class="btn-group">
        <button class="yes" @click="goToLove">
          YES ❤️
        </button>

        <button
          class="no"
          :style="noStyle"
          @touchstart.prevent="moveNo"
          @click.prevent="moveNo"
        >
          No 😢
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'
import FloatingHearts from '~/components/FloatingHearts.vue'

const router = useRouter()
const noStyle = ref({})

const moveNo = () => {
  const btnWidth = 120
  const btnHeight = 55

  const maxX = window.innerWidth - btnWidth - 10
  const maxY = window.innerHeight - btnHeight - 10

  let x = Math.random() * maxX
  let y = Math.random() * maxY

  // шанс "упасть вниз"
  if (Math.random() > 0.75) {
    y = maxY - 5
  }

  noStyle.value = {
    position: 'fixed',
    left: x + 'px',
    top: y + 'px'
  }
}

onMounted(() => {
  moveNo()
})

const goToLove = () => {
  router.push('/love')
}
</script>

<style>
html, body, #__nuxt {
  margin: 0;
  padding: 0;
  height: 100%;
}
</style>

<style scoped>
.container {
  height: 100vh;
  width: 100vw;
  background: linear-gradient(135deg, #ff4e88, #ffb6c1);
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  position: relative;
  font-family: Arial, sans-serif;
}

.card {
  background: rgba(255, 255, 255, 0.95);
  padding: 30px;
  border-radius: 20px;
  text-align: center;
  width: 90%;
  max-width: 350px;
  box-shadow: 0 15px 40px rgba(0,0,0,0.25);
  z-index: 2;
}

h1 {
  font-size: 22px;
  margin-bottom: 30px;
  color: #ff2f6d;
}

.btn-group {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

button {
  padding: 16px;
  border: none;
  border-radius: 40px;
  font-size: 18px;
  cursor: pointer;
}

.yes {
  background: #ff2f6d;
  color: white;
  transition: 0.3s;
}

.yes:active {
  transform: scale(0.95);
}

.no {
  background: #eee;
  color: #333;
  transition: 0.2s ease;
}
</style>
