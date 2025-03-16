<template>
  <div class="p-6">
    <!-- Page Header -->
    <header class="mb-8">
      <h1 class="text-2xl font-bold text-gray-900">Dashboard</h1>
      <p class="mt-1 text-sm text-gray-500">Welcome back, here's an overview of your CRM data.</p>
    </header>

    <!-- Stats Cards -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
      <div v-for="stat in stats" :key="stat.name" class="bg-white rounded-lg shadow p-6">
        <div class="flex items-center">
          <div class="flex-shrink-0">
            <i :class="[stat.icon, 'text-2xl text-indigo-600']"></i>
          </div>
          <div class="ml-4">
            <h2 class="text-sm font-medium text-gray-500">{{ stat.name }}</h2>
            <p class="mt-1 text-xl font-semibold text-gray-900">{{ stat.value }}</p>
          </div>
        </div>
        <div class="mt-4">
          <div class="flex items-center text-sm">
            <span :class="stat.change >= 0 ? 'text-green-600' : 'text-red-600'">
              <i :class="stat.change >= 0 ? 'fas fa-arrow-up' : 'fas fa-arrow-down'"></i>
              {{ Math.abs(stat.change) }}%
            </span>
            <span class="ml-2 text-gray-500">from last month</span>
          </div>
        </div>
      </div>
    </div>

    <!-- Recent Activity -->
    <div class="bg-white rounded-lg shadow">
      <div class="px-6 py-4 border-b border-gray-200">
        <h3 class="text-lg font-medium text-gray-900">Recent Activity</h3>
      </div>
      <div class="divide-y divide-gray-200">
        <div v-for="activity in recentActivity" :key="activity.id" class="px-6 py-4">
          <div class="flex items-center space-x-4">
            <div class="flex-shrink-0">
              <i :class="[activity.icon, 'text-lg text-indigo-600']"></i>
            </div>
            <div class="flex-1">
              <p class="text-sm font-medium text-gray-900">{{ activity.title }}</p>
              <p class="text-sm text-gray-500">{{ activity.description }}</p>
            </div>
            <div class="text-sm text-gray-500">
              {{ activity.time }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// Sample stats data
const stats = ref([
  {
    name: 'Total Contacts',
    value: '1,234',
    icon: 'fas fa-users',
    change: 12
  },
  {
    name: 'Active Leads',
    value: '456',
    icon: 'fas fa-user-plus',
    change: -2.5
  },
  {
    name: 'Tasks Due',
    value: '23',
    icon: 'fas fa-tasks',
    change: 8
  },
  {
    name: 'Deals Closed',
    value: '$45.2k',
    icon: 'fas fa-chart-line',
    change: 15.3
  }
])

// Sample activity data
const recentActivity = ref([
  {
    id: 1,
    icon: 'fas fa-user-plus',
    title: 'New Lead Created',
    description: 'John Smith from Acme Corp was added as a new lead',
    time: '5 min ago'
  },
  {
    id: 2,
    icon: 'fas fa-tasks',
    title: 'Task Completed',
    description: 'Follow-up call with Sarah Johnson completed',
    time: '1 hour ago'
  },
  {
    id: 3,
    icon: 'fas fa-dollar-sign',
    title: 'Deal Closed',
    description: 'Enterprise deal with TechCorp finalized',
    time: '2 hours ago'
  },
  {
    id: 4,
    icon: 'fas fa-calendar',
    title: 'Meeting Scheduled',
    description: 'Product demo scheduled with potential client',
    time: '3 hours ago'
  }
])
</script>
