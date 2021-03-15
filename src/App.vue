<template>
  <h1>Speed reaction timer</h1>
  <button @click="startgame" :disabled="isplaying">play</button>
  <Block v-if="isplaying" @result="setScore" :delay="delay" />
  <Result v-if="showResult" :score="score" />
</template>

<script>
import Block from "./components/block"
import Result from "./components/result"

export default {
  components: {Block , Result},
  data() {
    return{
      isplaying : false,
      delay : 0,
      score : 0,
      showResult : false
    }
  },
  methods : {

    startgame() {
      this.delay = Math.random() * (5000 - 2000) + 2000
      this.isplaying = true
      this.showResult = false
    },
    setScore(data) {
      this.isplaying = false
      this.score = data
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

button {
    background: #0faf87;
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
