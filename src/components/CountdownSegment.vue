<script setup>
defineProps({
  label: String,
  number: Number,
})
</script>

<template>
  <div class="segment text-center">
    <div class="pt-10 overflow-hidden relative">
      <Transition>
        <span :key="number" class="numbers text-green absolute top-0 left-[50%]">{{ number }}</span>
      </Transition>
    </div>

    <span class="label block pt-2">{{ label }}</span>
  </div>
</template>

<style>
.segment {
  width: 80px;
}
.numbers {
  transform: translateX(-50%);
  font-size: 32px;
}
.label {
  font-size: 16px;
}

.v-enter-active,
.v-leave-active {
  transition: transform 0.5s ease;
}
.v-enter-from {
  transform: translateY(-100%) translateX(-50%);
}
.v-leave-to {
  transform: translateY(100%) translateX(-50%);
}
</style>
