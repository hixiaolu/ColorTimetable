<script setup lang="ts">
import { weekTitle } from '~/stores/course'

const { currentMonth, originalWeekIndex, currentWeekIndex, originalWeekWeekIndex, currentWeekDayArray } = storeToRefs(useCourseStore())
</script>

<template>
  <div class="h-10 shadow-sm grid px-1 top-0 gap-1 grid-cols-[0.7fr_repeat(7,1fr)]">
    <div class="flex font-medium text-sm items-center justify-center">
      {{ `${currentMonth}月` }}
    </div>
    <div
      v-for="(item, index) in currentWeekDayArray" :key="index"
      class="border-y-transparent border-x-none flex flex-col border-t-4 border-b-4 text-xs transition-all duration-300 justify-evenly items-center"
      :class="originalWeekIndex === currentWeekIndex && originalWeekWeekIndex === index ? 'bg-light-blue-200 !border-b-light-blue-500 dark:bg-opacity-50' : ''"
    >
      <p class="font-medium">
        {{ weekTitle[index] }}
      </p>
      <p>{{ item }}</p>
    </div>
  </div>
</template>
