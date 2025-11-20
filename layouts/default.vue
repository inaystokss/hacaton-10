<template>
  <div class="flex min-h-screen text-gray-800">
    <!-- Боковое меню -->
    <aside
      v-if="isMenuOpen"
      class="fixed top-0 left-0 w-60 h-full shadow-lg flex flex-col items-center py-6 z-40"
    >
      <!-- Логотип -->
      <img src="/city.jpg" class="w-20 h-20 mb-4 rounded-full shadow" alt="Logo" />.
      <!-- Навигация -->
      <nav class="flex flex-col space-y-2 w-full text-center">
        <NuxtLink
          to="/"
          class="p-2 rounded transform transition-all duration-300 ease-in-out hover:bg-gray-300 hover:text-gray-900 hover:scale-105"
          :class="{ 'bg-gray-400 font-semibold text-white scale-105': route.path === '/' }"
        >
          🏠 Home
        </NuxtLink>

        <NuxtLink
          to="/lab3"
          class="p-2 rounded transform transition-all duration-300 ease-in-out hover:bg-gray-300 hover:text-gray-900 hover:scale-105"
          :class="{ 'bg-gray-400 font-semibold text-white scale-105': route.path === '/lab3' }"
        >
          🧪 Lab3
        </NuxtLink>

        <NuxtLink
          to="/lab4"
          class="p-2 rounded transform transition-all duration-300 ease-in-out hover:bg-gray-300 hover:text-gray-900 hover:scale-105"
          :class="{ 'bg-gray-400 font-semibold text-white scale-105': route.path === '/lab4' }"
        >
          🧩 Lab4
        </NuxtLink>

        <NuxtLink
          to="/lab5"
          class="p-2 rounded transform transition-all duration-300 ease-in-out hover:bg-gray-300 hover:text-gray-900 hover:scale-105"
          :class="{ 'bg-gray-400 font-semibold text-white scale-105': route.path === '/lab5' }"
        >
          ⚙️ Lab5
        </NuxtLink>

        <NuxtLink
          to="/lab6"
          class="p-2 rounded transform transition-all duration-300 ease-in-out hover:bg-gray-300 hover:text-gray-900 hover:scale-105"
          :class="{ 'bg-gray-400 font-semibold text-white scale-105': route.path === '/lab6' }"
        >
          📷 Lab6
        </NuxtLink>
      </nav>

      <div class="w-4/5 h-px bg-gray-400 my-4"></div>

      <!-- Кнопки Login / Logout -->
      <div class="flex flex-col space-y-2 w-full text-center">
        <button
          v-if="!isLoggedIn"
          @click="login"
          class="p-2 rounded bg-green-400 hover:bg-green-500 transition text-white font-medium"
        >
          🔑 Login
        </button>

        <button
          v-else
          @click="logout"
          class="p-2 rounded bg-red-400 hover:bg-red-500 transition text-white font-medium"
        >
          🚪 Logout
        </button>
      </div>
    </aside>

    <!-- Кнопка бургера -->
    <div
      class="fixed top-4 left-4 z-50 bg-gray-100 rounded-lg p-2 shadow cursor-pointer hover:bg-gray-200 transition"
      @click="toggleMenu"
    >
      <span v-if="!isMenuOpen">☰</span>
      <span v-else>✖</span>
    </div>

    <!-- Основной контент -->
    <main class="flex-1 p-8">
      <Transition name="fade" mode="out-in">
        <slot />
      </Transition>
    </main>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const isMenuOpen = ref(true)
const isLoggedIn = ref(false)

function toggleMenu() {
  isMenuOpen.value = !isMenuOpen.value
}

function login() {
  isLoggedIn.value = true
  alert('Вы вошли в систему!')
}

function logout() {
  isLoggedIn.value = false
  alert('Вы вышли из системы!')
}
</script>

<style>
body {
  background-color: #d1d5db;
  background-image: url('/6_black.jpg');
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  background-repeat: no-repeat;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.6s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>