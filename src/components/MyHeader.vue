<template>
  <header class="d-flex">
    <div class="logo-text">BOOLFLIX</div>
    <div class="input-container">
      <input class="input-bar" type="text" v-model="inputValue" placeholder="Inserisci un titolo" @keyup.enter="$emit('callApi', inputValue)"/>
      <i @click="ereaseInput" class="fa-regular fa-circle-xmark"></i>
    </div>
    
  </header>
</template>

<script>
    export default {
        name: 'MyHeader',
        data() {
            return {
               inputValue: '',
            }
        },
        methods: {
          ereaseInput() {
            this.inputValue = ''
          }
        }    
    }
</script>

<style lang="scss">
@import './styles/Common.scss';

  header {
    height: 80px;
    background-color: black;
    justify-content: space-between;
    align-items: center;
    padding: 20px;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    z-index: 999;

    .input-bar {
      border-radius: 5px;
      padding: 4px;
    }

    .fa-circle-xmark {
      color: red;
      margin-left: 10px;
    }

    .logo-text {
      color: red;
      font-size: 2rem;
    }
  }

</style>