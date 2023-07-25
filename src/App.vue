<template>

  <h1>Reaction Timer</h1>
  <button type="button" @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResoult" :score="score"/>
</template>

<script>

import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  components:{Block, Results},
  data(){
    return{
      delay: null,
      isPlaying: false,
      showResoult: false,
      score: null,
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResoult = false;
    },
    endGame(reactionTime){
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResoult = true;
    },
  }

}

</script>

<style>
body {
  margin: 0 0;
  padding: 0 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button {
  background-color: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
