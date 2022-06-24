<template>
  <div id="app">
    <!-- Header -->
    <header>
      
    </header>

    <div class="card-container">
      <div class="card" v-for="(item, index) in mySongsList" :key="index">
        <img src="" alt="">
        <p class="titolo"> {{item.title}} </p>
        <p class="font-small"> {{item.author}} </p>
        <p class="font-small"> {{item.year}} </p>
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
  text-align: center;
}

header {
  background-color: #2e3a46;
  height: 80px;
}
.card-container {
  padding: 100px 0;
  background-color: #1e2d3b;
  display: flex;
  justify-content: space-around;
}

.card {
  background-color: #2e3a46;
  padding: 10px;
  color: white;
  margin: 10px;
}

.titolo {
  font-size: 14px;
}

.font-small {
  font-size: 10px;
  color: grey;
}
</style>
