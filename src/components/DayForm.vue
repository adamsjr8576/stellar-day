<template>
  <form>
    <section class='date-input' v-if='displayForm'>
      <input v-model='date' type='date' />
      <button @click='submitDate()' type='button'>Change Date</button>
      <img class='down-arrow' @click='toggleDisplay()' :src='downArrow' />
    </section>
    <section class='display-new-date' v-else>
      <p>Select</p>
      <img class='up-arrow' @click='toggleDisplay()' :src='upArrow' />
      <p>Date</p>
    </section>
  </form>
</template>

<script>
  import upArrow from '../images/uploading.png';
  import downArrow from '../images/down-arrow.png';

  export default {
    name: 'header',
    data() {
      return {
        upArrow: upArrow,
        downArrow: downArrow,
        displayForm: false,
        date: ''
      }
    },
    methods: {
      toggleDisplay() {
        this.displayForm = !this.displayForm;
      },

      submitDate() {
        this.$emit('update:date', this.date);
        this.displayForm = false;
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
    height: 10vh;
  }

  .date-input {
    width: 100%;
    position: fixed;
    height: 500px;
    background-color: rgba(20, 20, 20, .95);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
  }

  input {
    margin-top: 30px;
    width: 20%;
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
    cursor: pointer;
    transition: transform 1s;
  }

  button:hover {
    transform: scale(1.02);
    box-shadow: 5px 4px #989AA4;
    transition: transform 1s;
  }

  button:active {
    transform: scale(.98);
    transform: translate(3px, 2px);
  }

  .display-new-date {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
  }

  .down-arrow {
    margin-top: 45px;
    height: 60px;
    width: auto;
    cursor: pointer;
    transition: transform 1s;
  }

  .down-arrow:hover {
    transform: scale(1.1);
    transition: transform 1s;
  }

  .up-arrow {
    height: 60px;
    width: auto;
    margin: 0 30px;
    cursor: pointer;
    transition-property: margin, transform;
    transition-duration: 1s, 1s;
  }

  .up-arrow:hover {
    transform: scale(1.1);
    margin: 0 15px;
    transition-property: margin, transform;
    transition-duration: 1s, 1s;
  }

  p {
    margin: 0;
  }

</style>
