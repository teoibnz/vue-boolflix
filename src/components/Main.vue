<template>
    <div>
        <ul v-for='(film, index) in filmList' :key="index" >
            <li>
                <img :src="filmPoster(film.poster_path)" alt="film poster">
            </li>
            <li>{{film.title || film.name}}</li>
            <li>{{film.original_title || film.original_name}}</li>
            <li>
                <country-flag :country='flags(film.original_language)' size='big'/>
            </li>
            <li v-for="star in 5 - getStars(film.vote_average)" :key='star'>
                <font-awesome-icon class="mb-3" icon="fa-solid fa-star" />
            </li>
        </ul>
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