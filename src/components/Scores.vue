<script setup>
import { defineProps, ref, onMounted } from 'vue';

const props = defineProps(['teamName', 'socket']);
const score = ref(0);

let teamName = props.teamName;



onMounted(() => {
const socket = new WebSocket('ws://localhost:3000/primus');
  // get data from websocket
  socket.onmessage = function (event) {
    console.log('Teamname:', teamName);
    let newData = JSON.parse(event.data);
    if(teamName === teamName){
        console.log("this team " + teamName);
    }
    if (newData.action == 'updatePoints') {
      if (newData.teamName == teamName) {
        score.value = newData.points;

      }
    }
  };
});
</script>

<template>
  <div class="scores">
    <h2>{{ teamName }}</h2>
    <p>Sporting Wolvertem</p>
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
