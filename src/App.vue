<template>
<!-- <NewForm/> -->
<div>
<h1>{{title}}</h1>
<p>{{subtitle}}</p>
<button @click="start" :disabled="isPlaying">Play</button>
<BlockCut v-if="isPlaying" :delay="delay" @end="endGame"/>
<ShowResults v-if="showResults" :score="score"/>
</div>

</template>

<script>
import BlockCut from "./components/BlockCut.vue"
import ShowResults from "./components/ShowResults.vue"
// import NewForm from "./components/NewForm.vue"
export default {
  name: 'App',
  components: { BlockCut, ShowResults},
  data(){
    return{
      title: "Reaction Timer",
      subtitle: "click on the box to see how fast you can react",
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    
    }
   
  },
   methods: {
      start(){
        this.delay = 2000 + Math.random()* 5000
        this.isPlaying= true;
         this.showResults= false
       
      },
      endGame(reactionTimer){
        this.score= reactionTimer
       this.isPlaying= false
         this.showResults= true
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

div{
  
  margin: 0 auto;
  width: 50%;
  background:whitesmoke;
  color: grey;
}

button{
  background: crimson;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin:10px;
}

button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
