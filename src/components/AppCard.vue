@@ -0,0 +1,19 @@
<script>
export default {
    props:{
        cardObj: Object,
    },
}
</script>

<template>
    <div class="card-container">
        <div class="card">
            <p>Titolo: {{ this.cardObj.title }}</p>
            <p>Titolo originale: {{ this.cardObj.original_title }}</p>
            <p>Lingua: {{ this.cardObj.original_language }}</p>
            <p>Voto: {{ this.cardObj.vote_average }}</p>
        </div>
    </div>
</template>

<style lang="scss" scoped>

</style>