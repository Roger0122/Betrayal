<template>
  <div class="p-6">
    <h1 class="text-4xl font-bold mb-6 text-center">密教小工具</h1>
    <div class="grid grid-cols-6 gap-4">
      <SyndicateCharacter
        v-for="char in characters"
        :key="char.name"
        :character="char"
        @click="selectCharacter(char)"
      />
    </div>

    <CharacterModal v-if="selected" :character="selected" @close="selected = null" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import SyndicateCharacter from '@/components/SyndicateCharacter.vue'

import CharacterModal from '@/components/CharacterModal.vue'
import characterData from '@/assets/character-data.json'

const characters = ref([])
const selected = ref(null)

function selectCharacter(char) {
  selected.value = char
}

onMounted(() => {
  characters.value = characterData
})
</script>

<style scoped>
.grid-cols-6 {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
}
</style>