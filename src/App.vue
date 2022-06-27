<template>
  <div id="app">

    <TheHeader></TheHeader>
    <TheAlbums></TheAlbums>

  </div>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import TheAlbums from "./components/TheAlbums.vue"

export default {
  name: 'App',
  components: {
    TheHeader,
    TheAlbums
}
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
