<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      click me
  </div>
</template>

<script>
export default {
    props: ['delay'], 
    data(){
        return{
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted(){
        console.log('component mounted')
        setTimeout(()=>{
            this.showBlock = true
            this.startTimer()
        }, this.delay)
    },
    methods: {
        startTimer(){
            this.timer = setInterval(()=>{
                this.reactionTime+=10
            }, 10)
            console.log("test")
        },
        stopTimer(){
             clearInterval(this.timer)
             this.$emit('end', this.reactionTime)
        }
    },
    update(){
    },
    unmounted(){
        
    }
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background-color: #2c3e50;
        color: #fff;
        text-align: center;
        cursor: pointer;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>