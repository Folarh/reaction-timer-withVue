<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click me
    </div>
</template>

<script>
export default {
    props: ["delay"],
    data(){
       return{
         showBlock: false,
         timer: null,
         reactionTimer: 0
       }
        },

    mounted(){
        setTimeout(()=>{
            this.showBlock= true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer(){
            this.timer= setInterval(()=>{
                this.reactionTimer += 10
            },10)
        },
        stopTimer(){
            clearInterval(this.timer)
          this.$emit('end', this.reactionTimer)
        }
    }
}
</script>

<style scoped>
.block{
    max-width: 400px;
    height: 150px;
    margin: 0 auto;
    border-radius: 20px;
    background: steelblue;
    color: white;
    text-align: center;
  
  
}
</style>