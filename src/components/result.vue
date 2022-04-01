<template>
  <p>Reaction Time {{score}} ms</p>
  <p class="rank">{{rank}}</p>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return{
            rank: null
        }
    },
    mounted(){
        if(this.score < 300){
            this.rank = 'ARE BHA BHAI BHAI !!'
    } else if (this.score < 400){
        this.rank = "Thik THIK H bhai"
    } else {
        this.rank = "Kya kar raha hai tu"
    }
    }
}
</script>

<style>
    .rank {
        font-size: 1.4em;
        font-weight: bold;
        color: #2c3e50;
    }
</style>