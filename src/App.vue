<script setup>
import Scores from './components/Scores.vue';

</script>

<template>
        <h1>Scoreboard</h1>
        <div class="scoreboard">
            <Scores teamName="team1" id="team1"/>
            <Scores teamName="team2" id="team2"/>
        </div>
    
</template>

<style scoped>
.scoreboard{
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    flex-direction: row;
    width: 100%;
    height: 100%;
    background-color: #fff;
    border-radius: 1rem;
    box-shadow: 0 0 1rem rgba(0,0,0,0.2);
}
</style>
