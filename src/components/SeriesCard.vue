@@ -0,0 +1,19 @@
<script>
export default {
    
    props:{
        cardObj: Object,
    },


    methods: {
        showFlag(curFlag){
            let imgUrl = ""
            switch(curFlag){
                case "en":
                    imgUrl = "../src/assets/img/Inghilterra.png"
                    break;
                case "it":
                    imgUrl = "../src/assets/img/Italia.png"
                    break; 
                case "fr":
                    imgUrl = "../src/assets/img/Francia.png"
                    break; 
                case "es":
                    imgUrl = "../src/assets/img/spagna.png"
                    break;
                default:
                    imgUrl = "../src/assets/img/Sconosciuta.png"   
            }
            return imgUrl
        },

        voteToStars(vote){
            vote = Math.floor(vote / 2) + 1;
            if (vote < 0){
                return 0
            } else if (vote > 5)
                return 5
            else {
                return vote
            }
        }
    }
}
</script>

<template>
    <div class="card-container">
        <div class="card">
            <img :src="`https://image.tmdb.org/t/p/w342${cardObj.poster_path}`" alt="Series poster">
            <p>Titolo: {{ this.cardObj.name }}</p>
            <p>Titolo originale: {{ this.cardObj.original_name }}</p>
            <p>Lingua:</p>
            <img :src="showFlag(cardObj.original_language)" alt="">
            <p>Voto: {{ this.cardObj.vote_average }}</p>
            <span v-for="curStar in voteToStars(this.cardObj.vote_average)"><i class="fa-solid fa-star"></i></span>
            <span v-for="curStar in (5 - voteToStars(this.cardObj.vote_average))"><i class="fa-regular fa-star"></i></span><br>
        </div>
    </div>
</template>

<style lang="scss" scoped>

</style>