<template>
    <div id="app">
    <!-- Header -->
        <header>
            <select class="form-select" aria-label="Default select example">
                <option selected>Scegli il genere</option>
                <option v-for="(item, index) in mySongsList" :key="index">
                {{item.genre}}
                </option>
            </select>
        </header>
    </div>
</template>


<script>
import axios from "axios";

export default {
    name: 'TheHeader',

    data () {
        return {
        apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
        mySongsList: [],
        genreList: []
        }
    },

    methods: { 
        fetchApp() {
        axios.get(this.apiUrl).then((resp) => {
            this.mySongsList = resp.data.response;
        })
        },
        getGenreList() {
        // funzione per togliere i doppioni di genere
        }
    },
    mounted() {
        this.fetchApp();
    }
}
</script>

<style scoped lang="scss">

header {
    background-color: #2e3a46;
    height: 80px;
    padding: 20px 500px;
    display: flex;
    justify-content: center;
}

</style>