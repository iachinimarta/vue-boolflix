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
      inputValueSaved: '',
    }
  },
  methods: {
    gettingFilms(inputValue) {
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=c9e49adea6145b4eeb6f6a272ae9bee6&query=' + inputValue + '&language=it')
        .then(reply => {
            this.rispostaApiFilm = reply.data.results;
            this.inputValueSaved = inputValue;
            this.gettingSeries();
            this.gettingFlags(this.rispostaApiFilm);
            this.gettingVoteAverage(this.rispostaApiFilm);
        })
        .catch(err => {
          console.log(err);
        });
    },
    gettingSeries() {
      axios.get('https://api.themoviedb.org/3/search/tv?api_key=c9e49adea6145b4eeb6f6a272ae9bee6&query=' + this.inputValueSaved + '&language=it')
      .then(reply => {
        this.rispostaApiSerieTv = reply.data.results;       
        this.gettingFlags(this.rispostaApiSerieTv);
        this.gettingVoteAverage(this.rispostaApiSerieTv);
      })
      .catch(err => {
        console.log(err);
      });
    },
    gettingFlags(array) {
      array.forEach(media => {
          if (media.original_language == 'it') {
            media.original_language = require('./assets/Flags/italy.png');
          } else if (media.original_language == 'fr') {
            media.original_language = require('./assets/Flags/france.png')
          } else if (media.original_language == 'de') {
            media.original_language = require('./assets/Flags/germany.png')
          } else if (media.original_language == 'en') {
            media.original_language = require('./assets/Flags/united_kingdom.png')
          } else {
            media.original_language = '?';
          }
        });   

    },
    gettingVoteAverage(array) {
      array.forEach(media => {
        media.vote_average = Math.round(media.vote_average / 2);
      });
    }             
  }
}
</script>

<style lang="scss">
  @import '~@fortawesome/fontawesome-free/css/all.css';
  @import './components/styles/Common.scss';
</style>
