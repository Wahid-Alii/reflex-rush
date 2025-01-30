<script setup>
import Block from '@/components/Block.vue'
import Results from '@/components/Results.vue'
import { ref } from 'vue'

const isPlaying = ref(false)
const delay = ref(null)
const score = ref(null)
const showResult = ref(false)

const start = () => {
  delay.value = 2000 + Math.random() * 5000
  isPlaying.value = true
  showResult.value = false
}
const endGame = (reactionTime) => {
  score.value = reactionTime
  isPlaying.value = false
  showResult.value = true
}
</script>

<template>
  <h1>Reflex Rush</h1>
  <button class="play-button" @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @stop="endGame" />
  <Results v-if="showResult" :score="score" />
</template>

<style>
#app {
  margin-top: 60px;
  text-align: center;
}
h1 {
  color: white;
  font-weight: bold;
}
.play-button {
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  border-radius: 12px;
}
.play-button:disabled {
  background-color: #cccccc;
  cursor: not-allowed;
}
</style>
