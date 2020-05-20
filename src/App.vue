<template>
  <div id="app">
    <StellarDay :favorites='favorites' :date='todayDate' @show:favorites='showFavorites = true'/>
    <Favorites
      v-if='showFavorites'
      :favorites='favorites'
      @hide:favorites='showFavorites = false'
      @display:selected='displaySelected'
    />
    <StellarImage
      v-else
      :imageInfo='imageInfo'
      :hasError='hasError'
      @toggle:favorites='toggleFavorites'
    />
    <DayForm v-if='!showFavorites' @update:date='resetDate'/>
  </div>
</template>

<script>
  import StellarDay from './components/StellarDay.vue';
  import StellarImage from './components/StellarImage.vue';
  import DayForm from './components/DayForm.vue';
  import Favorites from './components/Favorites.vue';

  const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
  const today = new Date();
  const date = today.toLocaleDateString("en-US", options);

  export default {
    name: 'App',
    components: {
      StellarDay,
      StellarImage,
      DayForm,
      Favorites
    },
    data() {
      return {
        imageInfo: {},
        todayDate: date,
        hasError: false,
        favorites: [],
        showFavorites: false
      }
    },
    mounted() {
      this.getImageInfo('');
    },
    methods: {
      async getImageInfo(date) {
        try {
          const response = await fetch(`https://api.nasa.gov/planetary/apod?api_key=8oQoPUrgzaFZKmMLnJAHgmp8kptIxV6YAC3CUceC${date}`);
          const data = await response.json();
          if (data.code === 400) {
            this.hasError = true;
          }
          const favoriteImageInfo = this.checkFavorites(data);
          this.imageInfo = favoriteImageInfo;
        } catch (error) {
          console.log(error)
        }
      },

      checkFavorites(imageInfo) {
        const check = this.favorites.filter(favorite => favorite.title === imageInfo.title);
        check.length === 1? imageInfo.favorite = true : imageInfo.favorite = false;
        return imageInfo;
      },

      toggleFavorites(imageInfo) {
        if (imageInfo.favorite) {
          imageInfo.favorite = false;
          this.favorites = this.favorites.filter(favorite => favorite.title !== imageInfo.title)
        } else {
          imageInfo.favorite = true;
          this.favorites.push(imageInfo);
        }
      },

      displaySelected(imageInfo) {
        console.log('made it')
        this.showFavorites = false;
        this.imageInfo = imageInfo;
      },

      resetDate(date) {
        this.hasError = false;
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
