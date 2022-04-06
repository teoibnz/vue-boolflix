<template>
  <div id="app">
    <Header @selectedFilms='newFilmSearch'/>
    <Main :filmList='filmsAndTV'/>
    
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
            tvList : null,
            filmsAndTV : [], 
            movieSearch : '',
        }
    },
    methods: {
      newFilmSearch(inputString){
        this.movieSearch = inputString;
        this.getFilmApi();
        this.getTvApi();
      },
      getFilmApi(){
          axios.get('https://api.themoviedb.org/3/search/movie?api_key=2a5f9472e37e691bde1b1ccea4b026fc&query=' + this.movieSearch)
          .then((result) => {
          this.filmList = result.data.results;
          this.filmsAndTV = [...this.filmList, ...this.tvList]
          console.warn(result)
          })
      },
      getTvApi(){
          axios.get('https://api.themoviedb.org/3/search/tv?api_key=2a5f9472e37e691bde1b1ccea4b026fc&query=`${userInput}`')
          .then((result) => {
          this.tvList = result.data.results;
          this.filmsAndTV = [...this.filmList, ...this.tvList]
          console.log(result)
          })
      }
    }
}
</script>

<style lang="scss">
@import './assets/styles/style.scss';
body{
  background-color: rgb(42, 42, 42);
}
</style>
