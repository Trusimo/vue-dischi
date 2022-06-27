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
            axios.get(this.apiUrl).then((resp) => {
                this.mySongsList = resp.data.response;
            }), console.log(this.fetchApp);
        },
        mounted() {
        this.fetchApp();
        console.log(this.mounted);
    },
        
        getGenreList() {
            let genreList = [];
            
            this.mySongsList.forEach((album) => {
                if (!genreList.includes(album.genre)) {
                genreList.push(album.genre);
                } console.log(this.getGenreList);
            });
            return genreList;
            },
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