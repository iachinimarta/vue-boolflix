<template>
  <div class="d-flex collection-container">
    <ul>
        <li v-for="(film, index) in rispostaApiFilm" :key="index">
            <h1>Film</h1>
            <ul>
                <li>Titolo: {{film.title}}</li>
                <li>Titolo originale: {{film.original_title}}</li>
                <li>Lingua: {{film.original_language}}</li>
                <li>Voto: {{film.vote_average}}</li>
                <img :src="urlBase + film.poster_path" :alt="film-title">
            </ul>
        </li>
    </ul>
    <ul>
        <li v-for="(serie, index) in rispostaApiSerieTv" :key="index">
            <h1>Serie Tv</h1>
            <ul>
                <li>Titolo: {{serie.name}}</li>
                <li>Titolo originale: {{serie.original_name}}</li>
                <li>Lingua: {{serie.original_language}}</li>
                <li>Voto: {{serie.vote_average}}</li>
                <img :src="urlBase + serie.poster_path" :alt="serie-title">
            </ul>
        </li>
    </ul>
  </div>
</template>

<script>
    export default {
        name: 'MyCollection',
        data() {
            return {
                urlBase: 'https://image.tmdb.org/t/p/w185'           
            }
        },
        props: {
            rispostaApiFilm: Array,
            rispostaApiSerieTv: Array,
        },
        methods: {
        }
    }
</script>

<style lang="scss">
    .collection-container {
        padding: 20px;
    }

</style>