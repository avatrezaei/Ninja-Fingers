<template>
  <h1>{{title}}</h1>
  
  <button @click="play" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" :delay="delay" @end="end" />
  <Results v-if="showResults" :score="score"/>
  
</template>

<script>

import myBlock from './components/Block.vue'
import myResults from './components/Results.vue'
export default {
  name: 'App',
  components: {
    Block : myBlock,
    Results : myResults
  },
  data(){
    return {
      isPlaying : false,
      showResults : false,
      delay : null,
      score : null
    }
  },
  methods:{
    play(){
      this.delay = 2000 + Math.random()*5000;
      this.isPlaying = true;
      console.log(this.delay);
      this.showResults = false;
    },
    end(reactionTime){
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    }
  }
}
</script>

<style>
#app, #modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
button{
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


button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
