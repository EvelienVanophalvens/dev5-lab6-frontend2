<script setup>
import { defineProps, ref, onMounted } from 'vue';

const props = defineProps(['teamName', 'socket']);
const score = ref(0);
const team = ref("");

let teamName = props.teamName;


onMounted(() => {
const socket = new WebSocket('ws://localhost:3000/primus');
  // get data from websocket
  socket.onmessage = function (event) {
    let newData = JSON.parse(event.data);
    console.log(newData);
    if (newData.action == 'updatePoints' && newData.teamName == teamName) {
        score.value = newData.points;
    }
    if (newData.action == 'updateTeam' && newData.teamName == teamName) {
        team.value = newData.selectedTeam;

    }
  };
});
</script>

<template>
  <div class="scores">
    <h2>{{ team }}</h2>
    <div class="score">
      {{ score }}
    </div>
  </div>
</template>

<style scoped>
.score {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: row;
  font-size: 10rem;
  font-weight: bold;
}
</style>
