<template>
  <header>
    <p>{{ date }}</p>
    <h1>Have a <u>STELLAR</u> day!</h1>
    <div>
      <button @click="$emit('show:favorites', true)">Favorites: {{ favorites.length }}
        <img class='favorite-star' :src='favoriteStar' alt='golden star icon' />
      </button>
    </div>
  </header>
</template>

<script>
  import favoriteStar from '../images/favoriteStar.png';

  export default {
    name: 'stellar-day',
    props: {
      date: String,
      favorites: Array
    },
    data() {
      return {
        favoriteStar: favoriteStar
      }
    }
  }
</script>

<style scoped>
  header {
    height: 10vh;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  h1 {
    margin: 0;
    font-size: 3em;
  }

  p {
    width: 20%;
  }

  button {
    width: 150px;
    font-size: 1.25em;
    display: flex;
    align-items: center;
    justify-content: space-around;
    border: 0;
    outline: 0;
    border-radius: 5px;
    padding: 5px;
    cursor: pointer;
  }

  button:hover {
    transform: scale(1.05);
    transition: transform 1s;
  }

  div {
    width: 20%;
  }

  .favorite-star {
    height: 20px;
    width: 20px;
  }
</style>
