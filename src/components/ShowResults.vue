<template>
  <p>Reaction Time: {{score}}ms</p>
  <p class="rank">{{rank}}</p>
</template>

<script>
export default {
props: ["score"],
data(){
    return{
        rank: null
    }
},
mounted(){
    if(this.score <250){
        this.rank= "King"
    }else if(this.score <400){
        this.rank= "monster"
    }else{
        this.rank= "snail...hahahahaa"
    }
}
}
</script>

<style>
.rank{
    font-size: 1.4em;
    color: crimson;
    font-weight: bold;
}
</style>
