<template>
  <form>
    <section class='date-input' v-if='displayForm'>
      <input v-model='date' type='date' />
      <button @click="$emit('update:date', date)" type='button'>Change Date</button>
    </section>
    <section class='display-new-date' v-else>
      <p>Select</p>
      <img @click='toggleDisplay()' :src='upArrow' />
      <p>Date</p>
    </section>
  </form>
</template>

<script>
  import upArrow from '../images/uploading.png';

  export default {
    name: 'header',
    data() {
      return {
        upArrow: upArrow,
        displayForm: false,
        date: ''
      }
    },
    methods: {
      toggleDisplay() {
        this.displayForm = !this.displayForm;
      }
    }

  }
</script>

<style scoped>
  form {
    display: flex;
    align-items: center;
    justify-content: space-around;
    width: 100%;
    font-size: 1.5em;
    height: 100px;
  }

  .date-input {
    width: 100%;
    position: fixed;
    height: 500px;
    background-color: rgba(200, 200, 200, .8);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
  }

  input {
    margin-top: 30px;
    width: 25%;
    border: 0;
    outline: 0;
    font-size: 1.5em;
    padding: 5px;
    border-radius: 5px;
  }

  button {
    margin-top: 40px;
    width: 20%;
    padding: 5px;
    font-size: 1.5em;
    border: 0;
    outline: 0;
    border-radius: 5px;
  }

  .display-new-date {
    display: flex;
    align-items: center;
    justify-content: space-around;
    width: 20%;
  }

  img {
    height: 60px;
    width: auto;
    cursor: pointer;
  }
</style>
