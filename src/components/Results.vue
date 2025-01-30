<script setup>
import { ref, onMounted } from 'vue';

const props = defineProps(['score'])
const ranking = ref(null)

onMounted(() => {
    if (props.score < 250) {
        ranking.value = 'Legendary'
    } else if (props.score < 350) {
        ranking.value = 'Good'
    } else {
        ranking.value = 'Slow'
    }
});
</script>

<template>
    <h3>Reaction time : {{ score }} ms</h3>
    <h1>{{ ranking }}</h1>
    <p>0-250 ms 'Legendary'</p>
    <p>251-350 ms 'Good'</p>
    <p>351 and above 'Slow'</p>
</template>

<style scoped>

h1 {
    color: white;
}
h3 {
    color: rgb(7, 68, 104);
    background-color: aqua;
    padding: 10px;
    border-radius: 5px;
    width: 250px;
    height: 50px;
    align-items: center;
    margin: 30px auto;
    font-weight: bold;
}
p {
    color: #85a7bb;
    padding: 10px;
    border-radius: 5px;
    margin: 10px 0;
    font-weight: bold;
    width: 250px;
    align-items: center;
    margin: auto;
}
</style>