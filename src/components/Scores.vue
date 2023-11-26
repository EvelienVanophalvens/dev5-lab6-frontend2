<script setup>
import { defineProps, ref } from 'vue';
const props = defineProps(['teamName', 'socket']);
const score = ref(0);
</script>

<template>
    <div class="scores">
        <h2>{{ teamName }}</h2>
        <p>Sporting Wolvertem</p>
        <div class="score">
            0
        </div>
    </div>
</template>

<style scoped>

.score{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    font-size: 10rem;
    font-weight: bold;
    
}
</style>