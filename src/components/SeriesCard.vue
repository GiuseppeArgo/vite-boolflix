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
        }
    }
}
</script>

<template>
    <div class="card-container">
        <div class="card">
            <p>Titolo: {{ this.cardObj.name }}</p>
            <p>Titolo originale: {{ this.cardObj.original_name }}</p>
            <p>Lingua:</p>
            <img :src="showFlag(cardObj.original_language)" alt="" v-if="showFlag(cardObj.original_language) != 'Bandiera non disponibile'">
            <p>Voto: {{ this.cardObj.vote_average }}</p>
        </div>
    </div>
</template>

<style lang="scss" scoped>

</style>