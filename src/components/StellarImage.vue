<template>
  <section>
    <p v-if='hasError'>{{ imageInfo.msg }} Please select another date.</p>
    <div v-else class='image-info-container'>
      <img class='stellar-image' :src='imageInfo.url' :alt='imageInfo.title' />
      <div class='text'>
        <img
          v-if='imageInfo.favorite'
          class='star'
          :src='favoriteStar'
          alt='golden star icon'
          @click="$emit('toggle:favorites', imageInfo)"
        />
        <img
          v-else
          class='star'
          :src='emptyStar'
          alt='empty star icon'
          @click="$emit('toggle:favorites', imageInfo)"
        />
        <h2>{{ imageInfo.title }}</h2>
        <p>{{ imageInfo.explanation }}</p>
        <p>Date: {{ imageInfo.date }}</p>
      </div>
    </div>
  </section>
</template>

<script>
  import emptyStar from '../images/emptyStar.png';
  import favoriteStar from '../images/favoriteStar.png';

  export default {
    name: 'header',
    props: {
      imageInfo: Object,
      hasError: Boolean,
    },
    data() {
      return {
        emptyStar: emptyStar,
        favoriteStar: favoriteStar
      }
    }
  }
</script>

<style scoped>
  .image-info-container {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-around;
  }

  section {
    display: flex;
    align-items: center;
    justify-content: space-around;
    width: 100%;
    min-height: 600px;
  }

  .star {
    height: 30px;
    width: 30px;
    cursor: pointer;
  }

  .stellar-image {
    height: auto;
    width: 60%;
    max-height: 600px;
  }

  .text {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    max-height: 600px;
    overflow: auto;
    width: 30%;
  }

  p {
    width: 100%;
    max-height: 450px;
    overflow: auto;
  }

</style>
