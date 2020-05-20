<template>
  <section>
    <p v-if='hasError'>{{ imageInfo.msg }} Please select another date.</p>
    <div v-else class='image-info-container'>
      <img :src='imageInfo.url' :alt='imageInfo.title' />
      <div class='text'>
        <h2>{{ imageInfo.title }}</h2>
        <p>{{ imageInfo.explanation }}</p>
        <p>Date: {{ imageInfo.date }}</p>
      </div>
    </div>
  </section>
</template>

<script>
  export default {
    name: 'header',
    props: {
      imageInfo: Object,
      hasError: Boolean
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

  img {
    height: auto;
    width: 60%;
    max-height: 600px;
  }

  .text {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    max-height: 500px;
    overflow: auto;
    width: 30%;
  }

  p {
    width: 100%;
    max-height: 450px;
    overflow: auto;
  }

</style>
