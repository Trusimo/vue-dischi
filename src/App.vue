<template>
  <div id="app">
    <!-- Header -->
    <header>

    </header>

    <div class="card-container">
      <div class="card">
        <img src="" alt="">
        <h1>Titolo canzone</h1>
        <p>Artista</p>
        <p>Anno</p>
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
      mySongsList: ""
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
    this.apiUrl
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
}

.card {
  background-color: #2e3a46;
  width: 100px;
  height: 300px;
}
</style>
