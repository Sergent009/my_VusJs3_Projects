<template>
<div class="container">
  <header>
    <h1>Rock, Paper, Scissor</h1>
  </header>

  <main class="container2">
    <div class="game" v-if="choice === null">

      <button  class="buttonRock" @click="play('rock')">
        ROCK
      </button>

      <button class="buttonPaper" @click="play('paper')">
        PAPER
      </button>

      <button class="buttonScissor" @click="play('scissor')">
        SCISSOR
      </button>
      <br><br>
       <div class="score">
        WINS : DRAWS : LOSSES<br/>
        &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
        {{wins}} &nbsp; &nbsp; :&nbsp; &nbsp;  {{draws}} &nbsp; &nbsp; :&nbsp; &nbsp;  {{losses}}<br/>
        Win Percentage -  &nbsp;{{winPercentage}} %
      </div>

    </div>

    <div v-else>
      <div class="text">
        You picked--<span class="innertext1"> {{ choice }}</span>
      </div>

      <div class="text">
        The computer picked--<span class="innertext2"> {{ computerChoice }}</span>
      </div>

      <div class="verdictText">
        {{ verdict }}
      </div>

      <button class="buttonReset" @click="resetRound">Reset</button>

      <div class="score">
        WINS : DRAWS : LOSSES<br/>
        &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
        {{wins}} &nbsp; &nbsp; :&nbsp; &nbsp;  {{draws}} &nbsp; &nbsp; :&nbsp; &nbsp;  {{losses}}<br/>
        Win Percentage -  &nbsp;{{winPercentage}} %
      </div>
    </div>

  </main>
</div>
</template>

<script>
import {ref,computed, onMounted} from 'vue'

export default {
  name: 'App',

  setup(){
    const wins = ref(0)
    const draws = ref(0)
    const losses = ref(0)

    const choice = ref(null)
    const computerChoice = ref(null)
    const verdict = ref(null)

    const outcomes = {
      rock: {
        rock: 'draw',
        paper: 'loss',
        scissor: 'win',
      },
      paper: {
        rock: 'win',
        paper: 'draw',
        scissor: 'loss',
      },
      scissor: {
        rock: 'loss',
        paper: 'win',
        scissor: 'draw',
      }
    }

    const winPercentage = computed(() => {
      const total = wins.value + draws.value + losses.value
      return (total ? (wins.value/total) * 100 : 0).toFixed(2)
    })

    const play = c => {
      choice.value = c

      const choices = ['rock', 'paper', 'scissor']
      const random = Math.floor(Math.random() * choices.length)
      computerChoice.value = choices[random]

      const outcome = outcomes[c][computerChoice.value]

      if(outcome == 'win'){
        wins.value++
        verdict.value = 'You win!'
      }
      else if(outcome == 'loss'){
        losses.value++
        verdict.value = 'You lose!'
      }
      else{
        draws.value++
        verdict.value = 'It is a draw!'
      }

      saveGame()
    }

    const saveGame = () => {
      localStorage.setItem('wins', wins.value)
      localStorage.setItem('draws', draws.value)
      localStorage.setItem('losses', losses.value)
    }

    const loadGame = () => {
      wins.value = localStorage.setItem('wins')
      draws.value = localStorage.setItem('draws')
      losses.value = localStorage.setItem('losses')
    }

    const resetRound = () => {
      computerChoice.value = null
      verdict.value = null
      choice.value = null
    }

    onMounted(() => {
      loadGame()

      window.addEventListener('keypress', e => {
        if(e.key === 'r'){
          resetRound()
        }
      })
    })

     return {
    wins,
    draws,
    losses,
    choice,
    computerChoice,
    verdict,
    play,
    resetRound,
    winPercentage
  };
 }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Teko:wght@300&display=swap');

.container{
  background: #333;
  color: #fff;
  position: absolute;
  top: 0;
  left: 0;
  width: 1300px;
  height: 668px;
}

header{
  text-align: center;
  font-size: 25px ;
  font-family: 'Teko', sans-serif;
  color: #333;
  background: white;
}

.game{
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 60px;
  padding: 0 50px;
}

.buttonRock{
  width: 200px;
  height: 200px;
  border: 2px solid black;
  border-radius: 50%;
  margin-right: 50px;
  font-size: 28px;
  color: white;
  font-family: 'Teko', sans-serif;
  cursor: pointer;
}
.buttonRock:hover{
  background: rgb(153, 87, 98);
  color: black;
}
.buttonPaper{
  width: 200px;
  height: 200px;
  border: 2px solid black;
  border-radius: 50%;
  margin-right: 50px;
  font-size: 28px;
  color: white;
  font-family: 'Teko', sans-serif;
  cursor: pointer;
}
.buttonPaper:hover{
  background: goldenrod;
  color: black;
}
.buttonScissor{
  width: 200px;
  height: 200px;
  border: 2px solid black;
  border-radius: 50%;
  font-size: 28px;
  color: white;
  font-family: 'Teko', sans-serif;
  cursor: pointer;
}
.buttonScissor:hover{
  background: rgb(50, 129, 50);
  color: black;
}

.text{
  display: flex;
  justify-content: center;
  text-align: center;
  font-size: 30px;
  font-family: 'Teko', sans-serif;
}

.innertext1{
  color: rgb(168, 74, 89);
  font-family: 'Teko', sans-serif;
}
.innertext2{
  color: green;
  font-family: 'Teko', sans-serif;
}

.verdictText{
  font-size: 35px;
  margin-top: 20px;
  color: yellow;
  width: 300px;
  height: 40px;
  background: #999696;
  border: 2px solid black;
  border-radius: 5px;
  position: absolute;
  top: 37%;
  left: 38%;
  text-align: center;
  font-family: 'Teko', sans-serif;
}

.buttonReset{
  position: absolute;
  top: 85%;
  left: 42%;
  width: 200px;
  height: 40px;
  font-size: 30px;
  color: #2c2b2b;
  border: 2px solid black;
  border-radius: 5px;
  font-family: 'Teko', sans-serif;
  background: black;
}
.buttonReset:hover{
  background: #2c2b2b;
  color: black;
}

.score{
  font-family: 'Teko', sans-serif;
  font-size: 40px;
  color: white;
  position: absolute;
  top: 55%;
  left: 41%;
}

</style>