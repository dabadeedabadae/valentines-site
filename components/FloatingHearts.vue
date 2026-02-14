<template>
  <div class="hearts">
    <div
      v-for="n in 40"
      :key="n"
      class="heart"
      :style="randomStyle()"
    >
      ❤️
    </div>
  </div>
</template>

<script setup>
const randomStyle = () => {
  const left = Math.random() * 100
  const duration = 5 + Math.random() * 5
  const delay = Math.random() * 5
  const size = 14 + Math.random() * 18

  return {
    left: left + '%',
    animationDuration: duration + 's',
    animationDelay: delay + 's',
    fontSize: size + 'px'
  }
}
</script>

<style scoped>
.hearts {
  position: absolute;
  width: 100%;
  height: 100%;
  overflow: hidden;
  pointer-events: none;
}

.heart {
  position: absolute;
  bottom: -50px;
  animation: floatUp linear infinite;
}

@keyframes floatUp {
  from {
    transform: translateY(0);
    opacity: 1;
  }
  to {
    transform: translateY(-110vh);
    opacity: 0;
  }
}
</style>
