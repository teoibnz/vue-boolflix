<template>
    <header>
        <input  v-model.trim="userInput" @keyup.enter="$emit('selectedFilms', userInput)" type="text">
        <button href="" class="btn btn-secondary mx-2">Search Movies</button>
        <select name="" id="">
            <option value="film">Films</option>
            <option value="serieTv">Tv Series</option>
        </select>
    </header>
</template>

<script>
export default {
    name : 'IndexHeader',
    data: function(){
        return {
            userInput : '',
            searchedFilms: '',
        }
    },
    methods : {
    }
}
</script>

<style scoped lang='scss'>

</style>