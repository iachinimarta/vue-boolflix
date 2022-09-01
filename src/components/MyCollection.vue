<template>
  <div>
    <div class="collection-container">
        <div class="media-container d-flex f-wrap">
            <div class="element" v-for="(film, index) in rispostaApiFilm" :key="index">
                <div class="wrapper">
                    <div class="img-null d-flex" v-if="film.poster_path == null">
                        <p class="text-no-img">{{film.title}}</p>
                    </div>
                    <img class="poster-img" v-else :src="urlBase + film.poster_path" :alt="film.title">
                    
                    <div class="overlay">
                        <span class="description word-wrap">
                            <ul class="description-text">                                
                                <li><img class="lang-img" :src="film.original_language" :alt="film.original_language"></li>
                                <li>Categoria: Film</li>
                                <li>Titolo: {{film.title}}</li>
                                <li v-show="!film.title == film.original_name">Titolo originale: {{film.original_title}}</li>
                                <li>Overview:</li>
                                <li class="overview-section">{{film.overview}}</li>
                                <li>
                                    Voto: <i v-for="n in 5" :key="n" class="fa-star" :class="(film.vote_average > n)?'fa-solid':'fa-regular'" ></i>
                                </li>
                            </ul>
                        </span>
                    </div>
                </div>
                <h4 class="word-wrap">{{film.title}}</h4>
            </div>

        </div>

        <div class="d-flex f-wrap media-container">

            <div class="element" v-for="(serie, index) in rispostaApiSerieTv" :key="index">

                <div class="wrapper">
                    <div class="img-null d-flex" v-if="serie.poster_path == null">
                        <p class="text-no-img">{{serie.name}}</p>
                    </div>
                    <img class="poster-img" v-else :src="urlBase + serie.poster_path" :alt="serie.name">
                    
                    <div class="overlay">
                        <span class="description word-wrap">
                            <ul>                                
                                <li><img class="lang-img" :src="serie.original_language" :alt="serie.original_language"></li>
                                <li>Categoria: Serie Tv</li>
                                <li v-show="!serie.name == serie.original_name">Titolo originale: {{serie.original_name}}</li>
                                <li>Overview:</li>
                                <li class="overview-section">{{serie.overview}}</li>
                                <li>
                                    Voto: <i v-for="n in 5" :key="n" class="fa-star" :class="(serie.vote_average > n)?'fa-solid':'fa-regular'" ></i>
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

        .media-container {
            justify-content: center;
            
            .element {
                margin: 10px;
                cursor: pointer;

                .wrapper {
                    position: relative;
                    border: 1px solid white;

                    &:hover .overlay {
                        display: block;
                    }

                    .img-null {
                        height: 300px;
                        width: 200px;
                        background-color: red;
                        justify-content: center;
                        align-items: center;
                        
                        .text-no-img {
                            font-size: 20px;
                        }
                    }

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
                            color: white;

                            .fa-star {
                                color: gold;
                            }
                        
                            .overview-section {
                                width: 150px;
                                display: -webkit-box;
                                -webkit-box-orient: vertical;
                                -webkit-line-clamp: 6; 
                                overflow: hidden;
                            }

                            .lang-img {
                                width: 25px;
                            }
                        }
                    }
                }
                
                .word-wrap {
                    width: 200px;
                    word-wrap: break-word;
                }
            }
        }
    }
</style>