<template>
  <div id="app">
    <StellarDay :date='todayDate'/>
    <StellarImage :imageInfo='imageInfo'/>
    <DayForm @update:date='resetDate'/>
  </div>
</template>

<script>
  import StellarDay from './components/StellarDay.vue';
  import StellarImage from './components/StellarImage.vue';
  import DayForm from './components/DayForm.vue';

  const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
  const today = new Date();
  const date = today.toLocaleDateString("en-US", options);

  export default {
    name: 'App',
    components: {
      StellarDay,
      StellarImage,
      DayForm
    },
    data() {
      return {
        imageInfo: {},
        todayDate: date
      }
    },
    mounted() {
      this.getImageInfo();
    },
    methods: {
      async getImageInfo(date) {
        if (date === undefined) {
          date = '';
        }
        try {
          const response = await fetch(`https://api.nasa.gov/planetary/apod?api_key=8oQoPUrgzaFZKmMLnJAHgmp8kptIxV6YAC3CUceC${date}`);
          const data = await response.json();
          this.imageInfo = data;
        } catch (error) {
          console.log(error);
        }
      },

      resetDate(date) {
        date = "&date=" + date;
        this.getImageInfo(date);
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
    color: #E9EAF1;
    height: 100%;
    width: 100%;
    background-color: rgb(20, 20, 20);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  body {
    height: 100vh;
    width: 100vw;
    margin: 0;
  }
</style>
