<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Navigation Sidebar - Only show when authenticated -->
    <Sidebar v-if="$route.name !== 'login'" />
    
    <!-- Main Content -->
    <main class="transition-all duration-200" :class="{ 'ml-64': $route.name !== 'login' }">
      <!-- Router View -->
      <router-view v-slot="{ Component }">
        <transition name="fade" mode="out-in">
          <component :is="Component" />
        </transition>
      </router-view>
    </main>
  </div>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'
import Sidebar from './components/Sidebar.vue'

// Component setup logic here
onMounted(() => {
  console.log('App mounted')
})
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.15s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
