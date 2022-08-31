<template>
  <div id="app">
    <MyHeader @callApiFilm="gettingFilms"/>
    <MyMain :rispostaApiFilm="rispostaApiFilm" :rispostaApiSerieTv="rispostaApiSerieTv"/>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue';
import MyMain from './components/MyMain.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain
  },
  data() {
    return {
      rispostaApiFilm: [],
      rispostaApiSerieTv: [],
      originalLanguage: [],
      inputValueSaved: '',
    }
  },
  methods: {
    gettingFilms(inputValue) {
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=c9e49adea6145b4eeb6f6a272ae9bee6&query=' + inputValue + '&language=it')
        .then(reply => {
            this.rispostaApiFilm = reply.data.results;
            this.inputValueSaved = inputValue;

            this.rispostaApiFilm.forEach(film => {
              film.vote_average = Math.round(film.vote_average / 2) ;
            });

            this.gettingSeries();
            this.gettingLanguage();
        })
        .catch(err => {
          console.log(err);
        });
    },
    gettingSeries() {
      axios.get('https://api.themoviedb.org/3/search/tv?api_key=c9e49adea6145b4eeb6f6a272ae9bee6&query=' + this.inputValueSaved + '&language=it')
      .then(reply => {
        this.rispostaApiSerieTv = reply.data.results;

        this.rispostaApiSerieTv.forEach(serie => {
              serie.vote_average = Math.round(serie.vote_average / 2);
            });
      })
      .catch(err => {
        console.log(err);
      });
    },
    gettingLanguage() {
      this.rispostaApiFilm.forEach(film => {
        if(!this.originalLanguage.includes(film.original_language)) {
          this.originalLanguage.push(film.original_language);
        }    
      });
    }                   
  }
}
</script>

<style lang="scss">
  @import '~@fortawesome/fontawesome-free/css/all.css';
  @import './components/styles/Common.scss';
</style>
