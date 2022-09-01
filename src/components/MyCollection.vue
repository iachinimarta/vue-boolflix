<template>
  <div>
    <div class="collection-container">
        <div class="films-container d-flex f-wrap">

            <div class="element" v-for="(film, index) in rispostaApiFilm" :key="index">

                <div class="wrapper">
                    <div class="img-null" v-if="film.poster_path == null">Nessuna immagine disponibile</div>
                    <img class="poster-img" v-else :src="urlBase + film.poster_path" :alt="film.title">
                    
                    <div class="overlay">
                        <span class="description word-wrap">
                            <ul class="description-text">
                                <li>Genere: Film</li>
                                <li>Titolo originale: {{film.original_title}}</li>
                                <li><img class="lang-img" :src="film.original_language" :alt="film.original_language"></li>
                                <li>
                                    <i v-for="n in 5" :key="n" class="fa-star" :class="(film.vote_average > n)?'fa-solid':'fa-regular'" ></i>
                                </li>
                            </ul>
                        </span>
                    </div>
                </div>
                <h4 class="word-wrap">{{film.title}}</h4>
            </div>

        </div>

        <div class="d-flex f-wrap series-container">

            <div class="element" v-for="(serie, index) in rispostaApiSerieTv" :key="index">

                <div class="wrapper">
                    <div class="img-null" v-if="serie.poster_path == null">Nessuna immagine disponibile</div>
                    <img class="poster-img" v-else :src="urlBase + serie.poster_path" :alt="serie.name">
                    
                    <div class="overlay">
                        <span class="description word-wrap">
                            <ul>
                                <li>Genere: Serie Tv</li>
                                <li>Titolo originale: {{serie.original_name}}</li>
                                <li><img class="lang-img" :src="serie.original_language" :alt="serie.original_language"></li>
                                <li>
                                    <i v-for="n in 5" :key="n" class="fa-star" :class="(serie.vote_average > n)?'fa-solid':'fa-regular'" ></i>
                                </li>
                            </ul>
                        </span>
                    </div>
                </div>
                <h4 class="word-wrap">{{serie.name}}</h4>
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

        .element {
            margin: 10px;
            cursor: pointer;
        }

        .wrapper {
            position: relative;
            border: 1px solid black;

            .poster-img {
                display: block;
                height: 300px;
            }

            .overlay {
                background-color: rgba(0, 0, 0, 0.8);
                width: 100%;
                height: 100%;
                position: absolute;
                top: 0;
                left: 0;
                display: none;

                .description {
                    font-weight: bold;
                    color: white;

                    .description-text {
                        padding: 20px;
                    }
                }
            }
            
        }

        .word-wrap {
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
            text-align: center;
        }
    }

    .wrapper:hover .overlay {
        display: block;
    }

</style>