<template>
  <div class="space-y-6">
    <!-- Page Header -->
    <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4">
      <div class="flex-1">
        <h1 class="text-2xl sm:text-3xl font-bold text-gray-900 dark:text-white">{{ isArabic ? 'مرحباً، مهند رشيد' : 'Welcome, Mohanad Rashid' }}</h1>
        <p class="text-gray-600 dark:text-gray-400 mt-1 text-sm sm:text-base">{{ isArabic ? 'إليك نظرة عامة على منظمة جودن' : 'Here\'s an overview of JODN organization' }}</p>
      </div>
      <div class="flex items-center space-x-3 space-x-reverse">
        <button class="btn-primary text-sm sm:text-base px-4 py-2 sm:px-6 sm:py-3">
          <PlusIcon class="h-4 w-4 sm:h-5 sm:w-5 ml-1 sm:ml-2" />
          <span class="hidden sm:inline">{{ isArabic ? 'إضافة مشروع جديد' : 'Add New Project' }}</span>
          <span class="sm:hidden">{{ isArabic ? 'إضافة' : 'Add' }}</span>
        </button>
      </div>
    </div>

    <!-- Stats Cards -->
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 sm:gap-6">
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
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-4 sm:gap-6">
      <!-- Projects Chart -->
      <div class="dashboard-card">
        <h3 class="text-lg font-semibold text-gray-900 dark:text-white mb-4">{{ isArabic ? 'المشاريع الشهرية' : 'Monthly Projects' }}</h3>
        <ProjectsChart />
      </div>

      <!-- Volunteers Chart -->
      <div class="dashboard-card">
        <h3 class="text-lg font-semibold text-gray-900 dark:text-white mb-4">{{ isArabic ? 'المتطوعين الجدد' : 'New Volunteers' }}</h3>
        <VolunteersChart />
      </div>
    </div>

    <!-- Budget and Recent Activity -->
    <div class="grid grid-cols-1 lg:grid-cols-3 gap-4 sm:gap-6">
      <!-- Budget Allocation -->
      <div class="dashboard-card">
        <h3 class="text-lg font-semibold text-gray-900 dark:text-white mb-4">{{ isArabic ? 'توزيع الميزانية' : 'Budget Allocation' }}</h3>
        <BudgetAllocationChart />
      </div>

      <!-- Recent Volunteers -->
      <div class="dashboard-card lg:col-span-2">
        <div class="flex items-center justify-between mb-4">
          <h3 class="text-lg font-semibold text-gray-900 dark:text-white">{{ isArabic ? 'آخر المتطوعين' : 'Recent Volunteers' }}</h3>
          <router-link to="/dashboard/volunteers" class="text-sm text-brand hover:text-brand-dark font-medium">
            {{ isArabic ? 'عرض الكل' : 'View All' }}
          </router-link>
        </div>
        <RecentVolunteers />
      </div>
    </div>

    <!-- Projects Performance -->
    <div class="dashboard-card">
      <h3 class="text-lg font-semibold text-gray-900 dark:text-white mb-4">{{ isArabic ? 'أداء المشاريع' : 'Projects Performance' }}</h3>
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
