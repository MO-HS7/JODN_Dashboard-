<template>
  <div class="stat-card">
    <div class="flex items-center justify-between">
      <div class="flex-1 min-w-0">
        <p class="text-xs sm:text-sm font-medium text-gray-600 dark:text-gray-400 truncate">{{ title }}</p>
        <p class="text-xl sm:text-2xl font-bold text-gray-900 dark:text-white mt-1 sm:mt-2">{{ value }}</p>
        <p v-if="change" class="text-xs sm:text-sm mt-1 sm:mt-2" :class="changeClass">
          {{ change }}
        </p>
      </div>
      <div class="flex-shrink-0 ml-2">
        <div class="w-10 h-10 sm:w-12 sm:h-12 rounded-lg flex items-center justify-center" :class="iconBg">
          <component :is="icon" class="h-5 w-5 sm:h-6 sm:w-6" :class="iconColor" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  title: {
    type: String,
    required: true
  },
  value: {
    type: [String, Number],
    required: true
  },
  change: {
    type: String,
    default: ''
  },
  changeType: {
    type: String,
    default: 'positive', // positive, negative, neutral
    validator: (value) => ['positive', 'negative', 'neutral'].includes(value)
  },
  icon: {
    type: [Object, Function],
    required: true
  },
  iconBg: {
    type: String,
    default: 'bg-blue-100 dark:bg-blue-900/30'
  },
  iconColor: {
    type: String,
    default: 'text-blue-600 dark:text-blue-400'
  }
})

const changeClass = computed(() => {
  const classes = {
    positive: 'text-green-600 dark:text-green-400',
    negative: 'text-red-600 dark:text-red-400',
    neutral: 'text-gray-600 dark:text-gray-400'
  }
  return classes[props.changeType] || classes.neutral
})
</script>
