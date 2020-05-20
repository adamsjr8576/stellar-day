<template>
  <section>
    <img :src='imageInfo.url' :alt='imageInfo.title' />
    <div>
      <h2>{{ imageInfo.title }}</h2>
      <p>{{ imageInfo.explanation }}</p>
      <p>Date: {{ imageInfo.date }}</p>
    </div>
  </section>
</template>

<script>
  export default {
    name: 'header',
    props: {
      imageInfo: Object
    }
  }
</script>

<style scoped>
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

  div {
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
