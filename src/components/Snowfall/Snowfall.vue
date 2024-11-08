<template>
  <div class="snow-container">
    <div
        v-for="flake in flakes"
        :key="flake.id"
        :style="flake.style"
        class="snowflake"
    >
      ❄️
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
    const flakes = ref([]);
    const generateFlakes = () => {
      for (let i = 0; i < 50; i++) {
        flakes.value.push({
          id: i,
          style: {
            left: `${Math.random() * 100}vw`,
            fontSize: `${Math.random() * 1.5 + 0.5}em`,
            animationDuration: `${Math.random() * 5 + 5}s`,
            animationDelay: `${Math.random() * 5}s`
          }
        });
      }
    };

    onMounted(generateFlakes);
</script>

<style scoped>
.snow-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  overflow: hidden;
}

.snowflake {
  position: absolute;
  top: -5vh;
  color: white;
  opacity: 0.8;
  animation-name: fall;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
}

@keyframes fall {
  to {
    transform: translateY(110vh);
  }
}
</style>
