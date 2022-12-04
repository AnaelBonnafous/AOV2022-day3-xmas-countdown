<script setup>
import CountdownHeader from '@/components/CountdownHeader.vue'
import CountdownSegment from './components/CountdownSegment.vue'
import { computed } from 'vue'
import { useNow } from '@vueuse/core'

const now = useNow()
const christmas = new Date('12/25/2022 00:00:00')

const remaining = computed(() => {
  let diff = Math.floor((christmas.getTime() - now.value.getTime()) / 1000)
  const seconds = diff % 60

  diff = Math.floor((diff - seconds) / 60)
  const minutes = diff % 60

  diff = Math.floor((diff - minutes) / 60)
  const hours = diff % 24

  diff = Math.floor((diff - hours) / 24)
  const days = diff

  return { days, hours, minutes, seconds }
})
</script>

<template>
  <div class="w-full h-full flex justify-center items-center p-10">
    <div>
      <div class="shadow-md relative bg-white p-5 rounded-lg border-gray-100 border-[1px]">
        <CountdownHeader />
        <main class="flex justify-center">
          <CountdownSegment label="days" :number="remaining.days" />
          <CountdownSegment label="hours" :number="remaining.hours" />
          <CountdownSegment label="minutes" :number="remaining.minutes" />
          <CountdownSegment label="seconds" :number="remaining.seconds" />
        </main>
      </div>
      <h4 class="mt-10 text-gray-400 text-center text-sm">
        This challenge brought to you by <a href="https://vueschool.io/" class="underline">Vue School</a>
      </h4>
    </div>
  </div>
</template>

<style>
div {
  display: block;
}
body {
  @apply bg-gray-100;
}
</style>
