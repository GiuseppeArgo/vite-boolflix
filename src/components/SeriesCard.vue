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
    <div class="series-card" :style="{backgroundImage: `url(https://image.tmdb.org/t/p/w342${cardObj.poster_path})` }">
        <div class="card-back p-2">
            <p>Titolo: {{ this.cardObj.name }}</p>
            <p>Titolo originale: {{ this.cardObj.original_name }}</p>
            <p class="overview">Trama: {{ this.cardObj.overview }}</p>
            <div class="mb-2 mt-3 text-center">
                <p>Lingua:</p>
                <img :src="showFlag(cardObj.original_language)" alt="" v-show="showFlag(cardObj.original_language) != 'Bandiera non disponibile'">
            </div>
            <div class="text-center">
                <p>Voto: {{ this.cardObj.vote_average }}</p>
                <span v-for="curStar in voteToStars(this.cardObj.vote_average)"><i class="fa-solid fa-star"></i></span>
                <span v-for="curStar in (5 - voteToStars(this.cardObj.vote_average))"><i class="fa-regular fa-star"></i></span><br>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.series-card {
    height: 600px;
    background-position: center;
    background-size: cover;
}

.card-back{
    display: none;
}

.series-card:hover .card-back {
    height: 600px;
    color: white;
    background-color: black;
    display: block;
    .overview {
        font-size: .6rem;
    }
    img {
        width: 50px;
    }
}
</style>