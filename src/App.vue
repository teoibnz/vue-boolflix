<template>
  <div id="app">
    <Header @selectedFilms='newFilmSearch'/>
    <Main :filmList='filmList'/>
    
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from 'axios';



export default {
  name: 'App',
  components: {
    Header,
    Main,
    
  },
  
    created: function(){
    this.getFilmApi();
    },
    data: function(){
        return {
            filmList : null,
            movieSearch : '',
        }
    },
    methods: {
      newFilmSearch(inputString){
        this.movieSearch = inputString;
        this.getFilmApi()
      },
      getFilmApi(){
          axios.get('https://api.themoviedb.org/3/search/movie?api_key=2a5f9472e37e691bde1b1ccea4b026fc&query=' + this.movieSearch)
          .then((result) => {
          this.filmList = result.data.results;
          console.warn(result)
          })
      },
      getTvApi(){
          axios.get('https://api.themoviedb.org/3/search/tv?api_key=2a5f9472e37e691bde1b1ccea4b026fc&query=`${userInput}`')
          .then((result) => {
          this.tvList = result.data.results;
          console.log(result)
          })
      }
    }
}
</script>

<style lang="scss">
@import './assets/styles/style.scss';

</style>
