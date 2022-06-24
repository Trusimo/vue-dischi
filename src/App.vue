<template>
  <div id="app">
    <!-- Header -->
    <header>
      
    </header>

    
      <div class="card-bg">
          <div class="container">
            <div class="row row-cols-5">
              <div class="col album-style" v-for="(item, index) in mySongsList" :key="index">
                <img class="img-fluid album-img" :src="item.poster" alt="">
                <span class="titolo text-center"> {{item.title}} </span>
                <span class="font-small text-center"> {{item.author}} </span>
                <span class="font-small text-center"> {{item.year}} </span>
              </div>
            </div>
          </div>
    </div>

  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'App',
  components: {
    
  },
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
      })
    }
  },
  mounted() {
    this.fetchApp();
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

header {
  background-color: #2e3a46;
  height: 80px;
}
.card-bg {
  background-color: #1e2d3b;
  padding: 50px;
}

.album-style {
  color:white;
  padding: 10px 60px;
  background-color: #2e3a46;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.album-img {
  height: 150px;
  width: 120px;
}

.titolo {
  font-size: 14px;
  padding: 10px 0;
}

.font-small {
  font-size: 10px;
  color: grey;
}
</style>
