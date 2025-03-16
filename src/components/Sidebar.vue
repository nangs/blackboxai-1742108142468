<template>
  <aside class="fixed top-0 left-0 h-screen w-64 bg-white border-r border-gray-200 transition-all duration-200 ease-in-out">
    <!-- Logo Section -->
    <div class="h-16 flex items-center justify-between px-4 border-b border-gray-200">
      <div class="flex items-center space-x-2">
        <i class="fas fa-cube text-indigo-600 text-2xl"></i>
        <span class="font-semibold text-xl text-gray-800">CRM Pro</span>
      </div>
    </div>

    <!-- Navigation Links -->
    <nav class="mt-6 px-4">
      <router-link 
        v-for="item in navigationItems" 
        :key="item.path"
        :to="item.path"
        class="flex items-center px-4 py-3 mb-2 text-gray-700 rounded-lg hover:bg-indigo-50 hover:text-indigo-600 transition-colors duration-200"
        :class="{ 'bg-indigo-50 text-indigo-600': $route.path === item.path }"
      >
        <i :class="[item.icon, 'w-5 h-5']"></i>
        <span class="ml-3">{{ item.name }}</span>
      </router-link>
    </nav>

    <!-- User Profile Section -->
    <div class="absolute bottom-0 left-0 right-0 p-4 border-t border-gray-200">
      <div class="flex items-center space-x-3">
        <div class="w-10 h-10 rounded-full bg-gray-200 flex items-center justify-center">
          <i class="fas fa-user text-gray-500"></i>
        </div>
        <div>
          <p class="text-sm font-medium text-gray-700">John Doe</p>
          <p class="text-xs text-gray-500">Administrator</p>
        </div>
      </div>
    </div>
  </aside>
</template>

<script setup lang="ts">
const navigationItems = [
  { name: 'Dashboard', path: '/', icon: 'fas fa-home' },
  { name: 'Contacts', path: '/contacts', icon: 'fas fa-address-book' },
  { name: 'Leads', path: '/leads', icon: 'fas fa-user-plus' },
  { name: 'Tasks', path: '/tasks', icon: 'fas fa-tasks' },
  { name: 'Reports', path: '/reports', icon: 'fas fa-chart-bar' },
  { name: 'Settings', path: '/settings', icon: 'fas fa-cog' }
]
</script>
