<template>
    <div>
        <FilmContainer :film= Object v-for='(element, index) in filmList' :key="index"/>
    </div>
</template>

<script>
import FilmContainer from './FilmContainer.vue'
import axios from 'axios';


export default {
    name : 'MainIndex',
    components : {
        FilmContainer
    },
    data: function(){
        return {
            filmList : null,
        }
    },
    created: function(){
    this.getFilmApi();
    },
    methods: {
    getFilmApi(){
        axios.get('https://api.themoviedb.org/3/movie/550?api_key=2a5f9472e37e691bde1b1ccea4b026fc')
        .then((result) => {
        this.filmList = result.data;
        console.log(this.filmList)
        })
    }}
}
</script>

<style scoped lang='scss'>

</style>