<template>
    <p>Reaction Time - {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
</template>

<script>
    export default{
        props:  {
            score: Number
        },
        data(){
            return {
                rank: null
            }
        },
        mounted(){
            if(this.score < 100){
                this.rank = "Ninja Finger";
            }else if(this.score < 200){
                this.rank = "Grasshopper Limps";
            }else if(this.score < 300){
                this.rank = "Beginner";
            }else{
                this.rank = "Noob";
            }
        },
        methods: {
        }
    }

</script>

<style scoped>
    p{
        font-size: 20px;
        color: #0faf87;
        font-weight: bold;
    }
    .rank{
        font-size: 1.4rem;
        color: #0faf87;
        font-weight: bold;
    }
</style>