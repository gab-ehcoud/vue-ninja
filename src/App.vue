<template>
  <h1>Hello World</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <result v-if="showResult" :score="score"/>
</template>

<script>

import block from './components/block.vue'
import result from './components/result.vue'

export default {
  name: 'App',
  components:  { block, result },
  data(){
    return {
      isPlaying: false,
      delay:null,
      score:null,
      showResult:false
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random()*5000
      this.isPlaying = true
      this.showResult = false
    },
    endGame(reactionTime){
      this.score=reactionTime
      this.isPlaying = false
      this.showResult = true
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
button{
  background-color: #2c3e50;
  color: #fff;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  margin: 10px;
  cursor: pointer;
}
button[disabled] {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
