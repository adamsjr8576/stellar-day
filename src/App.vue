<template>
  <div id="app">
    <Header />
    <StellarImage />
    <DayForm />
  </div>
</template>

<script>
  import Header from './components/Header.vue';
  import StellarImage from './components/StellarImage.vue';
  import DayForm from './components/DayForm.vue';

  export default {
    name: 'App',
    components: {
      Header,
      StellarImage,
      DayForm
    },
    data() {
      return {
        imageInfo: {}
      }
    },
    methods: {

    }
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: rgb(220, 220, 220);
    height: 100%;
    width: 100%;
    background-color: rgb(20, 20, 20);
  }

  body {
    height: 100vh;
    width: 100vw;
    margin: 0;
  }
</style>
