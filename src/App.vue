<template>
  <Navbar/>
  <MainList/>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import MainList from "./components/MainList.vue";

export default {
  name: 'App',
  components: {
    Navbar,
    MainList
  },
}
</script>

<style lang="scss">
  body {
    margin: 0;
    width: 100vw;
    height: 100vh
  }
  #app {
    width: 100%;
    height: 100%;
    display: flex;
  }
</style>
