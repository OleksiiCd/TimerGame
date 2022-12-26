<template>
  <h1>Перевір свою реакцію!</h1>
  <button @click="start" :disabled="isPlaying">Почати гру!</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score"/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  data(){
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  components:{ Block, Results }, 
              
  methods:{
    start(){
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 5000
      this.showResults = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
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
  color: #444;
  margin-top: 60px;
  
}
h1{
  width: 400px;
  padding: 20px 0;
  border: 2px dotted darkgrey;
  border-radius: 10px;
  padding: 25px auto;
  margin: 40px auto;
  text-align: center;
  color: black;
  background: wheat;
}
body{
  background: url(https://www.teahub.io/photos/full/276-2761552_one-plus-6-gradient-stock-4k-wallpapers-gradient.jpg);
}
p{
  width: 300px;
  margin: 25px auto;
  color: black;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  border-bottom: 1px solid darkgrey;
  border-radius: 10px;
  background: lightgray;
  
}
button{
  background: green;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
} 
</style>
