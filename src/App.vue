<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HomeHeader from './layouts/HomeHeader.vue'
import HomeFooter from './layouts/HomeFooter.vue'

import { ref, onMounted, onBeforeUnmount, onBeforeMount } from 'vue';
import { gsap } from 'gsap';

onBeforeMount(() => {
  const cursor = document.querySelector('cursor')
  const follower = document.querySelector('follower')

  document.addEventListener("mousemove", onMouseMove);

  // Event Handlers
  function onMouseMove(e) {
    // console.log(e.x, e.y);
    gsap.to(follower, 0.4, {
      x: e.clientX - 18,
      y: e.clientY - 18
    });
    gsap.to(cursor, 0.1, {
      x: e.clientX - 4,
      y: e.clientY - 4
    });
  }
})

// onBeforeUnmount(() => {
//   if (cursor) {
//     window.removeEventListener("mousemove", updateMousePosition);
//   }
// });

</script>

<template>
  <div>
    <HomeHeader></HomeHeader>
    <RouterView />
    <footer>My App Footer</footer>
  </div>

  <div class="cursor">
  </div>

  <div class="follower">
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}

.cursor {
  position: fixed;
  top: 0;
  left: 0;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background-color: #fff;
  z-index: 2000;
}

.follower {
  position: fixed;
  top: 0;
  left: 0;
  width: 100px;
  height: 100px;
  background-color: #0ef;
  border-radius: 50%;
  opacity: 0.7;
}
</style>
