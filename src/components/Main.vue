<template>
    <div class="container-fluid">
        <h3 class="text-white">ORIGINALI NETFLIX</h3>
        <div class="row" v-for='(film, index) in filmList' :key="index" >
            <span class="col-12">
                <img class="mt-4" :src="filmPoster(film.poster_path)" alt="film poster">
            </span>
            <div class="my-film-info">
                <span>{{film.title || film.name}}</span>
                <span>{{film.original_title || film.original_name}}</span>
                <span>
                    <country-flag :country='flags(film.original_language)' size='big'/>
                </span>
                <span v-for="star in 5 - getStars(film.vote_average)" :key='star'>
                    Rating : <font-awesome-icon class="mb-3" icon="fa-solid fa-star" />
                </span>
            </div>
            
        </div>
    </div>
</template>

<script>


export default {
    name : 'MainIndex',
    props: ['filmList'],
    data : function(){
        return {
            posterFirstUrl : 'https://image.tmdb.org/t/p/',
            posterSize : "w342",
        }
    },
    methods : {
        flags(name){
            let flag ='';
            if (name === 'en') flag = 'gb';
            else if (name === 'zh') flag = 'cn'
            else if (name === 'ja') flag = 'jp'
            else if (name === 'ko') flag = 'kp'
            else flag = name;
            return flag
        },

        filmPoster(poster){
            return this.posterFirstUrl + this.posterSize + `${poster}`
        },

        getStars(rating){
            return Math.ceil(rating / 2)
        }
    }
}
</script>

<style scoped lang='scss'>

</style>