<template>
    <main>
        <input type="text" v-model="inputValue"/>
        <button @click="callApi">Cerca</button>

        
        <div v-for="(film, index) in rispostaApi" :key="index">
            Titolo: {{film.title}} <br>
            Titolo originale: {{film.original_title}} <br>
            Lingua: {{film.original_language}} <br>
            Voto: {{film.vote_average}}
            <br>
            <hr>
        </div>
      
    </main>  
</template>

<script>
    import axios from 'axios';

    export default {
        name: 'MyMain',
        data() {
            return {
                inputValue: '',
                rispostaApi: [],
                imgSrc: ''
            }
        },
        methods: {
            callApi() {
                axios.get('https://api.themoviedb.org/3/search/movie?api_key=c9e49adea6145b4eeb6f6a272ae9bee6&query=' + this.inputValue + '&language=it')
                .then(reply => {
                    this.rispostaApi = reply.data.results;
                });
            },                         
        },
    }
</script>

<style lang="scss">

</style>