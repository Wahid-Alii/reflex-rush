<script setup>
import { ref, onMounted, defineEmits } from 'vue'

const props = defineProps(['delay', 'stop'])
const emit = defineEmits(['stop'])
const showBlock = ref(false)
const timer = ref(null)
const reactionTime = ref(0)

onMounted(() => {
    setTimeout(() => {
        showBlock.value = true
        startTimer()
    }, props.delay)
})
const startTimer = () => {
    timer.value = setInterval(() => {
        reactionTime.value += 10
    }, 10)
}
const stopTimer = () => {
    clearInterval(timer.value)
    emit('stop', reactionTime.value)
}
</script>

<template>
    <div class="block" v-if="showBlock" @click="stopTimer" :stop="reactionTime.vale">
        Click me
    </div>
</template>

<style>
.block {
    width: 200px;
    height: 200px;
    background-color: aqua;
    border-radius: 10px;
    color: black;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    margin: 40px auto;
    font-weight: bold;
    font-size: larger;
}
</style>