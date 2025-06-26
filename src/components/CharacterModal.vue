<template>
  <div class="fixed inset-0 bg-black bg-opacity-40 flex items-center justify-center z-50">
    <div class="bg-white rounded-xl p-6 shadow-lg w-[300px] text-center relative">
      <h2 class="text-2xl font-bold mb-4">{{ character.name }}</h2>

      <template v-if="character.best">
        <p class="mb-2 text-green-600">✅ 最佳部門：{{ character.best }}</p>
        <p class="mb-2 text-yellow-500">🟡 次要部門：{{ character.second }}</p>
      </template>

      <template v-else>
        <p class="text-red-600 font-semibold">❌ 請趕走它</p>
      </template>

      <button class="mt-4 px-4 py-2 bg-gray-800 text-white rounded" @click="$emit('close')">
        關閉
      </button>
    </div>
  </div>
</template>

<script setup>
defineProps({
  character: Object
})
</script>