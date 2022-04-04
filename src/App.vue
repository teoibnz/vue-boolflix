<template>
  <div id="app">
    <Header />
    <Main :film='element'/>
    
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
    methods: {
    getFilmApi(){
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=missions')
        .then((result) => {
        this.filmList = result.data.results;
        console.warn(result)
        })
    }}
}
</script>

<style lang="scss">
@import './assets/styles/style.scss';

</style>
