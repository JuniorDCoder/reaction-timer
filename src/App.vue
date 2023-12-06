<template>
  <h1>Ninga Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" :isPlaying="isPlaying" @end="endGame"/>
  <Results v-if="showResults" :score="score"/>
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: 'App',
  components: {
    Block,
    Results,
  },
  data(){
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  
  methods: {
    start(){
      this.delay = 2000 + Math.random() + 3000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime){
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    }
  },
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #444;
    margin-top: 60px;
    user-select: none;
  }
  button{
    background: #0faf87;
    color: white;
    border: none;
    padding: 8px 16px;
    font-size: 16px;
    border-radius: 4px;
    cursor: pointer;
    letter-spacing: 1px;
    margin: 10px;
  }
  button[disabled]{
    opacity: 0.2;
    cursor: not-allowed;
  }
</style>
