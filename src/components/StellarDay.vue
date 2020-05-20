<template>
  <header>
    <div></div>
    <h1>Have a <u>STELLAR</u> day!</h1>
    <p>{{ date }}</p>
  </header>
</template>

<script>
  export default {
    name: 'stellar-day',
    props: {
      date: String
    }
  }
</script>

<style scoped>
  header {
    height: 100px;
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

  div {
    width: 20%;
  }
</style>
