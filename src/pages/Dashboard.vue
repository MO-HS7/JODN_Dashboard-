<template>
  <div class="space-y-4 sm:space-y-6">
    <!-- Page Header -->
    <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-3 sm:gap-4 p-2 sm:p-0">
      <div class="flex-1">
        <h1 class="text-lg sm:text-2xl md:text-3xl font-bold text-gray-900 dark:text-white leading-tight">{{ isArabic ? 'مرحباً، مهند رشيد' : 'Welcome, Mohanad Rashid' }}</h1>
        <p class="text-gray-600 dark:text-gray-400 mt-1 text-xs sm:text-sm md:text-base">{{ isArabic ? 'إليك نظرة عامة على منظمة جودن' : 'Here\'s an overview of JODN organization' }}</p>
      </div>
      <div class="flex items-center space-x-2 sm:space-x-3 space-x-reverse mt-2 sm:mt-0">
        <button class="btn-primary text-xs sm:text-sm md:text-base px-3 py-2 sm:px-4 sm:py-2 md:px-6 md:py-3 w-full sm:w-auto">
          <PlusIcon class="h-3 w-3 sm:h-4 sm:w-4 md:h-5 md:w-5 ml-1 sm:ml-2" />
          <span class="hidden sm:inline">{{ isArabic ? 'إضافة مشروع جديد' : 'Add New Project' }}</span>
          <span class="sm:hidden">{{ isArabic ? 'إضافة' : 'Add' }}</span>
        </button>
      </div>
    </div>

    <!-- Stats Cards -->
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-3 sm:gap-4 md:gap-6 p-2 sm:p-0">
      <StatCard
        :title="isArabic ? 'إجمالي المشاريع' : 'Total Projects'"
        :value="24"
        :change="isArabic ? '+12% من الشهر الماضي' : '+12% from last month'"
        changeType="positive"
        :icon="FolderIcon"
        iconBg="bg-blue-100 dark:bg-blue-900/30"
        iconColor="text-blue-600 dark:text-blue-400"
      />
      <StatCard
        :title="isArabic ? 'المتطوعين النشطين' : 'Active Volunteers'"
        :value="156"
        :change="isArabic ? '+8 متطوعين جدد' : '+8 new volunteers'"
        changeType="positive"
        :icon="UserGroupIcon"
        iconBg="bg-green-100 dark:bg-green-900/30"
        iconColor="text-green-600 dark:text-green-400"
      />
      <StatCard
        :title="isArabic ? 'الميزانية المستخدمة' : 'Used Budget'"
        value="₪245,000"
        :change="isArabic ? '75% من الإجمالي' : '75% of total'"
        changeType="neutral"
        :icon="BanknotesIcon"
        iconBg="bg-yellow-100 dark:bg-yellow-900/30"
        iconColor="text-yellow-600 dark:text-yellow-400"
      />
      <StatCard
        :title="isArabic ? 'التقارير المنجزة' : 'Completed Reports'"
        :value="18"
        :change="isArabic ? '+3 هذا الأسبوع' : '+3 this week'"
        changeType="positive"
        :icon="DocumentTextIcon"
        iconBg="bg-purple-100 dark:bg-purple-900/30"
        iconColor="text-purple-600 dark:text-purple-400"
      />
    </div>

    <!-- Charts Row -->
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-3 sm:gap-4 md:gap-6 p-2 sm:p-0">
      <!-- Projects Chart -->
      <div class="dashboard-card">
        <h3 class="text-sm sm:text-base md:text-lg font-semibold text-gray-900 dark:text-white mb-3 sm:mb-4">{{ isArabic ? 'المشاريع الشهرية' : 'Monthly Projects' }}</h3>
        <ProjectsChart />
      </div>

      <!-- Volunteers Chart -->
      <div class="dashboard-card">
        <h3 class="text-sm sm:text-base md:text-lg font-semibold text-gray-900 dark:text-white mb-3 sm:mb-4">{{ isArabic ? 'المتطوعين الجدد' : 'New Volunteers' }}</h3>
        <VolunteersChart />
      </div>
    </div>

    <!-- Budget and Recent Activity -->
    <div class="grid grid-cols-1 lg:grid-cols-3 gap-3 sm:gap-4 md:gap-6 p-2 sm:p-0">
      <!-- Budget Allocation -->
      <div class="dashboard-card">
        <h3 class="text-sm sm:text-base md:text-lg font-semibold text-gray-900 dark:text-white mb-3 sm:mb-4">{{ isArabic ? 'توزيع الميزانية' : 'Budget Allocation' }}</h3>
        <BudgetAllocationChart />
      </div>

      <!-- Recent Volunteers -->
      <div class="dashboard-card lg:col-span-2">
        <div class="flex flex-col sm:flex-row sm:items-center justify-between mb-3 sm:mb-4 gap-2 sm:gap-0">
          <h3 class="text-sm sm:text-base md:text-lg font-semibold text-gray-900 dark:text-white">{{ isArabic ? 'آخر المتطوعين' : 'Recent Volunteers' }}</h3>
          <router-link to="/dashboard/volunteers" class="text-xs sm:text-sm text-brand hover:text-brand-dark font-medium">
            {{ isArabic ? 'عرض الكل' : 'View All' }}
          </router-link>
        </div>
        <RecentVolunteers />
      </div>
    </div>

    <!-- Projects Performance -->
    <div class="dashboard-card p-2 sm:p-0">
      <h3 class="text-sm sm:text-base md:text-lg font-semibold text-gray-900 dark:text-white mb-3 sm:mb-4">{{ isArabic ? 'أداء المشاريع' : 'Projects Performance' }}</h3>
      <ProjectsPerformanceChart />
    </div>
  </div>
</template>

<script setup>
import { PlusIcon, FolderIcon, UserGroupIcon, BanknotesIcon, DocumentTextIcon } from '@heroicons/vue/24/outline'
import StatCard from '@/components/dashboard/StatCard.vue'
import ProjectsChart from '@/components/dashboard/ProjectsChart.vue'
import VolunteersChart from '@/components/dashboard/VolunteersChart.vue'
import BudgetAllocationChart from '@/components/dashboard/BudgetAllocationChart.vue'
import RecentVolunteers from '@/components/dashboard/RecentVolunteers.vue'
import ProjectsPerformanceChart from '@/components/dashboard/ProjectsPerformanceChart.vue'
import { useTranslation } from '@/composables/useTranslation'

const { isArabic } = useTranslation()
</script>
