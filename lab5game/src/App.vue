<template>
  <div>
    <h1>เป่า ยิ้ง ฉุบ</h1>
    <button @click="playGame('hammer')">ค้อน</button>
    <button @click="playGame('paper')">กระดาษ</button>
    <button @click="playGame('scissors')">กรรไกร</button>
    <img :src="playerImgUrl" alt="Player choice" />
    <img :src="computerImgUrl" alt="Computer choice" />
    <p>{{ result }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const playerImgUrl = ref('src/assets/player.jpg');
const computerImgUrl = ref('src/assets/ai.png');
const result = ref('');

const choices = {
  rock: 'src/assets/hammer.jpg',
  paper: 'src/assets/paper.png',
  scissors: 'src/assets/scissors.png',
};


const playGame = (playerChoice) => {
  playerImgUrl.value = choices[playerChoice];
  
  const computerChoice = ['rock', 'paper', 'scissors'][Math.floor(Math.random() * 3)];
  computerImgUrl.value = choices[computerChoice];
  
  if (playerChoice === computerChoice) {
    result.value = 'Draw!';
  } else if (
    (playerChoice === 'rock' && computerChoice === 'scissors') ||
    (playerChoice === 'paper' && computerChoice === 'rock') ||
    (playerChoice === 'scissors' && computerChoice === 'paper')
  ) {
    result.value = 'You win!';
  } else {
    result.value = 'You lose!';
  }
};
</script>
