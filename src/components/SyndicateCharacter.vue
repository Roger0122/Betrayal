<template>
  <div
    class="border rounded p-2 hover:bg-gray-100 cursor-pointer text-center"
    @click="$emit('click')"
  >
    <img :src="imgSrc" @error="onImgError" class="w-16 h-16 mx-auto mb-2" alt="頭像" />
    <p class="font-semibold">{{ character.name }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const props = defineProps({ character: Object })

const hasError = ref(false)
const imgSrc = ref(`/images/${props.character.name}.png`)

function onImgError() {
  if (!hasError.value) {
    imgSrc.value = '/images/placeholder.png'
    hasError.value = true
  }
}
</script>