<template>
  <div id="app">
    <StellarDay />
    <StellarImage :imageInfo='imageInfo'/>
    <DayForm />
  </div>
</template>

<script>
  import StellarDay from './components/StellarDay.vue';
  import StellarImage from './components/StellarImage.vue';
  import DayForm from './components/DayForm.vue';

  export default {
    name: 'App',
    components: {
      StellarDay,
      StellarImage,
      DayForm
    },
    data() {
      return {
        imageInfo: {}
      }
    },
    mounted() {
      this.getImageInfo();
    },
    methods: {
      async getImageInfo() {
        try {
          const response = await fetch('https://api.nasa.gov/planetary/apod?api_key=8oQoPUrgzaFZKmMLnJAHgmp8kptIxV6YAC3CUceC');
          const data = await response.json();
          this.imageInfo = data;
        } catch (error) {
          console.log(error);
        }
      }
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
