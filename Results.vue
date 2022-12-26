<template>
  <p>Час реакції {{ score }} мілісекунд!</p>
  <p class="rank">{{ rank }}</p>
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
        if(this.score < 250){
            this.rank = "Швидкі пальці!"
        }else if(this.score < 400){
            this.rank = "Майже швидкі пальці!"
        }else{
            this.rank = "Якось тормозиш...Може кави?"
        }
    }
}
</script>

<style>
.rank{
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
}
</style>