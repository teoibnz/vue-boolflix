<template>
    <main>
        <h3 class="text-white">ORIGINALI NETFLIX</h3>
        <div class="container-fluid d-flex">
        <div class="row my-film-container position-relative overflowy-scroll" v-for='(film, index) in filmList' :key="index" >
            <span class="col-12">
                <img class="mt-4" :src="filmPoster(film.poster_path)" alt="film poster">
            </span>
            <div class="my-film-info p-5">
                <p  >{{film.title || film.name}}</p   >
                <p  >{{film.original_title || film.original_name}}</p >
                <p> {{film.overview}} </p>
                <span>
                    <country-flag :country='flags(film.original_language)' size='big'/>
                </span>
                <!-- <span v-for="star in 5 - getStars(film.vote_average)" :key='star'>
                    Rating : <font-awesome-icon class="mb-3" icon="fa-solid fa-star" />
                </span> -->
            </div>
            
        </div>
    </div>
    </main>
    
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


main{
    overflow-x: scroll;
    div.my-film-container{
        img{
            height: 479px;
        }

        .my-film-info{
            position: absolute;
            top: 40px;
            height: 80%;
            color: white;
            text-align: center;
            display: none;
        }
    } 
}
div.my-film-container:hover .my-film-info{
    display: inline-block;
}
div.my-film-container:hover img{
    opacity: 0.2;
    filter: blur(3px);
    transform: scale(1.1);
    z-index: 2;
}

</style>