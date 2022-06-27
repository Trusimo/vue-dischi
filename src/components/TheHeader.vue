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
        }
    },

    methods: { 
        fetchApp() {
            console.log("pippoo");
            axios.get(this.apiUrl).then((resp) => {
                this.mySongsList = resp.data.response;
            })
        },
        
        
        getGenreList() {
            console.log("paperino");
            let genreList = [];
            
            this.mySongsList.forEach((album) => {
                if (!genreList.includes(album.genre)) {
                genreList.push(album.genre);
                }
            });
            return genreList;
            },
        },
        mounted() {
            console.log("pluto");
                this.fetchApp();
            },
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