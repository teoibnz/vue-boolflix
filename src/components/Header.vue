<template>
    <header class='m-2 d-flex justify-content-between'>
        <img class="img-fluid p-2" src="https://image.tmdb.org/t/p/w342/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="">
        <div>
            <input class="bg-dark border-0 text-white mx-2" placeholder="Search" v-model.trim="userInput" @keyup.enter="$emit('selectedFilms', userInput)" type="text">
            <button @click="$emit('selectedFilms', userInput)" class="btn btn-secondary mx-2">Search Movies</button>
        </div>
    </header>
</template>

<script>
export default {
    name : 'IndexHeader',
    data: function(){
        return {
            userInput : '',
        }
    },
}
</script>

<style scoped lang='scss'>
header{
    height: 10vh;
    img{
        height: 50%;
    }
}
</style>