<template>
  <!-- <h2>This is Home View!</h2>
  <h1>{{ msg }}</h1> -->

  <header class="main-header">
    <div class="layers">
      <div class="layer__header">
        <div class="layer__caption">Welcome to Parallax</div>
        <div class="layer__title">Fairy Forest</div>
      </div>
      <div class="layer layers__sky"></div>
      <div class="layer layers__clouds-1"></div>
      <div class="layer layers__rocks"></div>
      <div class="layer layers__ground-1"></div>
      <div class="layer layers__ground-2"></div>
      <div class="layer layers__clouds-2"></div>
      <div class="layer layers__ground-3"></div>
      <div class="layer layers__plant"></div>
    </div>
  </header>

  <article class="main-article">
    <div class="main-article__content">
      <h2 class="main-article__header">
        To be continued...
      </h2>
      <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Assumenda dolores quisquam temporibus, corporis earum
        deserunt nobis. Nostrum delectus itaque sequi reiciendis iusto! Iusto ut ea nisi illum fugit at nam!</p>
    </div>
    <div class="copyright">☆*: .｡. o(≧▽≦)o .｡.:*☆</div>
  </article>

  <div class="main-content">
    <p>To Be Continued!</p>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

defineProps<{
  msg: string
}>()

// Define a ref for the scrollY value
const scrollY = ref(window.scrollY);

// Update the --scrollTop CSS variable when scrolling
const updateScrollTop = () => {
  scrollY.value = window.scrollY;
  document.body.style.cssText = `--scrollTop: ${scrollY.value}px`;
};

// Add a scroll event listener when the component is mounted
onMounted(() => {
  window.addEventListener('scroll', updateScrollTop);
});

// Remove the scroll event listener when the component is unmounted
onUnmounted(() => {
  window.removeEventListener('scroll', updateScrollTop);
});
</script>

<style scoped>
.main-header {
  position: relative;
}

.layer {
  height: 100%;
  width: 100%;
  position: absolute;
  background-size: cover;
  background-position: center;
}

.layers {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  overflow: hidden;
  position: relative;
}

.layers__ground-1 {
  background-image: url(../assets/background/ground_1.png);
  
}

.layers__ground-2 {
  background-image: url(../assets/background/ground_2.png);
  /* transform: translate3d(0, var(--scrollTop), 0); */
}

.layers__ground-3 {
  background-image: url(../assets/background/ground_3.png);
  /* transform: translate3d(0, var(--scrollTop), 0); */
}

.layers__clouds-1 {
  background-image: url(../assets/background/clouds_1.png);
}

.layers__clouds-2 {
  background-image: url(../assets/background/clouds_2.png);
}

.layers__plant {
  background-image: url(../assets/background/plant.png);
}

.layers__rocks {
  background-image: url(../assets/background/rocks.png);
}

.layers__sky {
  background-image: url(../assets/background/sky.png);
  transform: translate3d(0, calc(var(--scrollTop) / 1), 0);
  overflow: hidden;
}

.main-article {
  min-height: 100vh;
}
</style>