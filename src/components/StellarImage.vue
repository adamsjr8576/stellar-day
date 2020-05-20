<template>
  <section>
    <img :src='imageInfo.url' :alt='imageInfo.title' />
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
  img {
    height: 500px;
    width: auto;
  }

</style>
