<template>
  <nav
    class="w-full flex justify-between items-center fixed bg-[#DDD0C8] p-5 text-[#323232] z-50 border-b-0 border-[#323232] drop-shadow-lg"
  >
    <!-- Logo Section -->
    <a href="/" class="text-3xl">
      <img src="../assets/logo.png" alt="Logo" />
    </a>

    <!-- Mobile Menu Button -->
    <div class="md:hidden" @click="toggleMenu">
      <button class="focus:outline-none">
        <span class="text-3xl">☰</span>
      </button>
    </div>

    <!-- Navigation Links -->
    <ul
      :class="{
        hidden: !isMenuOpen && !isDesktop,
        flex: isMenuOpen || isDesktop,
        'flex-col': !isDesktop,
        'md:flex-row': isDesktop,
      }"
      class="md:flex md:items-center md:gap-10 pr-20 text-xl font-semibold transition-all duration-300"
    >
      <li v-for="item in navItems" :key="item" class="flex justify-around">
        <a href="#" class="hover:text-gray-700">{{ item }}</a>
      </li>
    </ul>
  </nav>
</template>

<script setup>
import { ref, onMounted } from "vue";

const navItems = ["Home", "About Me", "Skills", "Projects", "Contact"];
const isMenuOpen = ref(false);
const isDesktop = ref(false);

// Toggles the menu for mobile view
const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

// Detect if the screen size is desktop
const checkScreenSize = () => {
  isDesktop.value = window.innerWidth >= 768;
};

onMounted(() => {
  checkScreenSize();
  window.addEventListener("resize", checkScreenSize);
});
</script>
