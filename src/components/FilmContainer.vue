<template>
    <div> 
        <ul>
            <li>{{film.adult}}</li>
            <li>{{film.original_title}}</li>
            <li>{{film.original_language}}</li>
            <li>{{film.vote_average}}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name : 'FilmContainer',
    props: ['film']
}
</script>

<style>

</style>