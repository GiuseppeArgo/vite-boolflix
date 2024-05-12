<script>
import { store } from "../store"
export default {
    data() {
        return {
            store,
        }
    }
}
</script>

<template>
<div>
    <div class="header">
        <div class="container">
            <h1>BOOLFLIX</h1>
            <div class="search">
                <label for="search">Trova un film o una serie</label>
                <div>
                    <input v-model="store.searchQuery" id="search" type="text" placeholder="Cerca...">
                    <button @click="$emit('searchIn')">Trova</button>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<style lang="scss" scoped>
@use "../style/partials/variable" as *;
@use "../style/partials/mixin" as *;

.header {
    height: 80px;
    padding: 10px;
    background-color: black;
    color: white;

    .container {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin: 0 auto;

        h1 {
            color: red;
        }
        
        .search {
            display: flex;
            padding: 10px;
            

            label {
                margin-right: 10px;
                margin-top: 6px;
            }

            input {
                padding: 5px 2px;
            }

            button {
                padding: 5px 2px;
                background-color: white;
            }
        }
    }
}
</style>