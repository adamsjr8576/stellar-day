<template>
  <section class='favorites-section' v-if='favorites.length > 0'>
    <div>
      <button @click="$emit('hide:favorites', false)">Back</button>
    </div>
    <article v-for='favorite in favorites'
      :key='favorite.title'
      :style="{backgroundImage: `url(${favorite.url})`}"
      @click="$emit('display:selected', favorite)"
    >
      <p class='favorite-title'>{{ favorite.title }}</p>
    </article>
  </section>
  <section v-else class='no-favorites-section'>
    <button @click="$emit('hide:showFavorites', false)">Back</button>
    <p>You have no favorites!!</p>
  </section>
</template>

<script>

  export default {
    name: 'favorites',
    props: {
      favorites: Array
    }
  }
</script>

<style scoped>
  .favorites-section {
    height: 90vh;
    display: flex;
    align-items: center;
    justify-content: space-around;
    flex-wrap: wrap;
    overflow: auto;
  }

  div {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .no-favorites-section {
    height: 90vh;
  }

  button {
    width: 20%;
    font-size: 1.25em;
    padding: 5px;
    border-radius: 5px;
    border: 0;
    outline: 0;
    cursor: pointer;
  }

  article {
    height: 300px;
    width: 400px;
    background-size: cover;
    margin: 15px;
    display: flex;
    justify-content: center;
    align-items: flex-end;
    cursor: pointer;
    border-radius: 5px;
    transition: transform 1s;
  }

  article:hover {
    transform: scale(1.03);
    transition: transform 1s;
  }

  .favorite-title {
    font-size: 1.25em;
    width: 80%;
    background-color: rgba(30, 30, 30, .9);
    padding: 5px;
    border-radius: 5px;
  }
</style>
