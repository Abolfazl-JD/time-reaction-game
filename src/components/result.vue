<template>
    <div class="result">Reaction time - {{score}} ms</div>
    <br>
    <div class="rank">{{rank}}</div>
</template>

<script>
export default {
    props : ["score"],
    data() {
        return{
            rank : null
        }
    },
    mounted() {
        if(this.score < 250) this.rank = "you're very fast "
        else if(this.score < 350) this.rank = "you're a bit fast "
        else if(this.score < 500) this.rank = "you're slow "
        else this.rank = "you're super lazy "
    }
}
</script>

<style>

.rank {
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
  }
  .result{
      margin-top: 20px;
  }
</style>