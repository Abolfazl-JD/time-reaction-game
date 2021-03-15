<template>
  <div class="block" @click="showResult" v-if="showBlock">Click me</div>
</template>

<script>

export default {
    props : ["delay"],
    data() {
        return{
            showBlock : false,
            timer : null,
            reaction : 0
        }
    },
    mounted() {
        setTimeout(() => {
            this.showBlock = true
            this.startGame()
        }, this.delay);
    },
    methods : {
        startGame() {
            this.timer = setInterval(() => {
                this.reaction += 10
            }, 10);
        },
        showResult() {
            clearInterval(this.timer)
            this.$emit("result" , this.reaction)
        }
    }
}
</script>

<style>

.block {
    width: 400px;
    border-radius: 20px;
    background:  #0faf87;;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
    cursor: pointer;
  }    
</style>