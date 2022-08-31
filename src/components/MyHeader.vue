<template>
  <header class="d-flex">
    <div class="logo-text">BOOLFLIX</div>
    <div class="input-container">
      <input type="text" v-model="inputValue" placeholder="Inserisci un titolo.."/>
      <button @click="$emit('callApiFilm', inputValue)">Cerca</button>
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

    .logo-text {
      color: red;
      font-size: 2rem;
    }
  }

</style>