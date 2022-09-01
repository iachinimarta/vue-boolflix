<template>
  <div>
    <div class="collection-container">
        <h1>Film</h1>
        <div class="films-container d-flex f-wrap">
            <div v-for="(film, index) in rispostaApiFilm" :key="index">
                <div class="img-null" v-if="film.poster_path == null">Nessuna immagine disponibile</div>
                <img v-else :src="urlBase + film.poster_path" :alt="film.title">
                <ul>
                    <li class="title"><h2>{{film.title}}</h2></li>
                    <li class="title">Titolo originale: {{film.original_title}}</li>
                    <li><img class="lang-img" :src="film.original_language" :alt="film.original_language"></li>
                    <li>
                        <i v-for="n in 5" :key="n" class="fa-star" :class="(film.vote_average > n)?'fa-solid':'fa-regular'" ></i>
                    </li>
                </ul>
            </div>
        </div>

        <h1>Serie Tv</h1>
        <div class="d-flex f-wrap series-container">
            <div v-for="(serie, index) in rispostaApiSerieTv" :key="index">
                <div class="img-null" v-if="serie.poster_path == null">Nessuna immagine disponibile</div>
                <img v-else :src="urlBase + serie.poster_path" :alt="serie.name">
                <ul>
                    <li class="title"><h2>{{serie.name}}</h2></li>
                    <li class="title">Titolo originale: {{serie.original_name}}</li>
                    <li><img class="lang-img" :src="serie.original_language" :alt="serie.original_language"></li>
                    <li>
                        <i v-for="n in 5" :key="n" class="fa-star" :class="(serie.vote_average > n)?'fa-solid':'fa-regular'" ></i>
                    </li>
                </ul>
            </div>
        </div>
    </div>
    
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

        .title {
            width: 200px;
            word-wrap: break-word;
        }

        .img-null {
            height: 300px;
            width: 200px;
            background-color: yellow;
        }

        .lang-img {
            width: 25px;
        }
    }

</style>