<template>
    <p class="result">Reaction time: {{score}} ms</p>
    <p class="rank">{{rank}} ...</p>
    <p class="result"> Click play again to restart the game</p>
</template>

<script>
export default {
    name:'results',
    props: [
        'score'
    ],
    data(){
        return {
            rank: null
        }
    },
    mounted(){
        if(this.score < 250){
            this.rank = "Hayai"
        }
        else if(this.score < 500 ){
            this.rank = "Not Hayai"
        }
        else {
            this.rank = "Osoi"
        }
    }
}
</script>

<style scooped>
    .result {
        font-size: 1.2em;
        font-weight: 400;

    }
    .rank {
        font-size: 1.6em;
        font-weight: bold;
        color: #79B4B7;
    }
</style>