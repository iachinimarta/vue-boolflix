<template>
  <header>
    <input type="text" v-model="inputValue" placeholder="Inserisci un titolo.."/>
    <button @click="$emit('callApiFilm', inputValue)">Cerca</button>
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

<style>

</style>