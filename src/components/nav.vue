<script setup>
// Import Vue's Composition API helpers
import { ref, computed, onMounted, onUnmounted } from 'vue'

// Controls whether the slide-in menu is open
const isSlideMenuOpen = ref(false)

// Tracks current screen width for responsive logic
const screenWidth = ref(window.innerWidth)

// Update screen width on window resize
const updateScreenWidth = () => {
  screenWidth.value = window.innerWidth
}

// Listen for window resize when mounted, clean up when unmounted
onMounted(() => window.addEventListener('resize', updateScreenWidth))
onUnmounted(() => window.removeEventListener('resize', updateScreenWidth))

// Breakpoint conditions
const isDesktop = computed(() => screenWidth.value >= 1024)
const isTablet = computed(() => screenWidth.value >= 768 && screenWidth.value < 1024)
const isMobile = computed(() => screenWidth.value < 768)

// Toggle the slide menu open/closed
const toggleSlideMenu = () => {
  isSlideMenuOpen.value = !isSlideMenuOpen.value
}
</script>

<template>
  <nav>
    <!-- Site Logo -->
    <div class="logo">
      <img src="../assets/Logos/Logo White.svg" alt="SiteLogo" class="logo-img" />
    </div>

    <!-- Menu section -->
    <div class="right-side">
      <!-- Inline menu for desktop/tablet -->
      <ul class="menu inline-menu">
        <!-- Show full menu for desktop -->
        <template v-if="isDesktop">
          <li><a href="#">HOME</a></li>
          <li><a href="#">OUR SCREENS</a></li>
          <li><a href="#">SCHEDULE</a></li>
          <li><a href="#">MOVIE LIBRARY</a></li>
          <li><a href="#">LOCATION & CONTACT</a></li>
        </template>

        <!-- Shorter menu for tablet -->
        <template v-else-if="isTablet">
          <li><a href="#">HOME</a></li>
          <li><a href="#">OUR SCREENS</a></li>
          <li><a href="#">SCHEDULE</a></li>
          <li><a href="#">MOVIE LIBRARY</a></li>
        </template>
      </ul>

      <!-- Hamburger menu button for all views -->
      <button class="menu-button" @click="toggleSlideMenu"><img src="../assets/Icons/Menu White.svg" alt=""></button>

      <!-- Slide-in drawer menu -->
      <div class="slide-menu" :class="{ open: isSlideMenuOpen }" @click.self="toggleSlideMenu">
        <button class="close-button" @click="toggleSlideMenu"><img src="../assets/Icons/Close White.svg" alt=""></button>

        <ul>
          <!-- Extra link for desktop slide menu -->
          <li v-if="isDesktop">
            <a href="#" @click="toggleSlideMenu">GALLERY</a>
          </li>

          <!-- Extra links for tablet slide menu -->
          <template v-else-if="isTablet">
            <li><a href="#" @click="toggleSlideMenu">LOCATION & CONTACT</a></li>
            <li><a href="#" @click="toggleSlideMenu">GALLERY</a></li>
          </template>

          <!-- Full menu for mobile slide menu -->
          <template v-else>
            <li><a href="#" @click="toggleSlideMenu">HOME</a></li>
            <li><a href="#" @click="toggleSlideMenu">OUR SCREENS</a></li>
            <li><a href="#" @click="toggleSlideMenu">SCHEDULE</a></li>
            <li><a href="#" @click="toggleSlideMenu">MOVIE LIBRARY</a></li>
            <li><a href="#" @click="toggleSlideMenu">LOCATION & CONTACT</a></li>
            <li><a href="#" @click="toggleSlideMenu">GALLERY</a></li>
          </template>
        </ul>
      </div>
    </div>
  </nav>
</template>

<style scoped>
nav {
    position: relative;
    background: #000;
    color: white;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 20px 100px;
    border-bottom: 1px solid rgb(34, 34, 34);
}

.logo-img {
    height: 40px;
    width: auto;
}

.right-side {
    display: flex;
}

.menu {
    list-style: none;
    display: flex;
    gap: 20px;
    margin: 0;
    padding: 10px;
    padding-right: 30px;
}

.menu li a {
    color: white;
    font-weight: bold;
    text-decoration: none;
    letter-spacing: 2px;
    transition: color 0.3s;
}

.menu li a:hover {
    text-decoration: underline;
    color: #1e90ff;
}

.menu-button {
    font-size: 2rem;
    background: none;
    border: none;
    color: white;
    cursor: pointer;
}

.slide-menu {
    position: fixed;
    top: 0;
    right: 0;
    width: 320px;
    height: 100vh;
    background: #111;
    padding: 60px 20px 20px;
    transform: translateX(100%);
    transition: transform 0.4s ease-in-out;
    z-index: 10000;
    overflow-y: auto;
}

.slide-menu.open {
    transform: translateX(0);
}

.close-button {
    position: absolute;
    top: 15px;
    right: 15px;
    font-size: 1.8rem;
    background: none;
    border: none;
    color: white;
    cursor: pointer;
}

.slide-menu ul {
    list-style: none;
    padding: 0;
    margin: 0;
}

.slide-menu li {
    margin-bottom: 20px;
}

.slide-menu a {
    color: white;
    text-decoration: none;
    font-weight: bold;
    letter-spacing: 2px;
}

.slide-menu a:hover {
    color: #1e90ff;
    text-decoration: underline;
}

@media (min-width: 768px) and (max-width: 1023px) {
  nav {
    padding: 20px 30px;
  }
}


@media (max-width: 767px) {
    nav {
        padding: 15px 20px;
    }
}
</style>
