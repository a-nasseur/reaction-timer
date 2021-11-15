<template>
  <h1>{{title}}</h1><br>
  <p>Welcome to the reaction time ultimate test</p>
  <p>Click on the play button, and wait, when the time comes you will have</p>
  <p>to click as fast as you can</p><br>
  <button class="btn" @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay = delay @end="endGame"/>
  <Results v-if="showScore" :score = score />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {Block, Results},
  data() {
    return {
      title: 'Reaction Timer App',
      isPlaying: false,
      delay: null,
      score: null,
      showScore: false
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000 
      this.isPlaying = true
      this.showScore = false

    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showScore = true
    }
  }
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.btn {
  background-color: #79B4B7;
  border: none;
  padding: 20px;
  width: 150px;
  border-radius: 5px;
  color: white;
  font-size: 1.2em;
}

P {
  font-size: 1.2em;
  font-weight: 500;
}

</style>
