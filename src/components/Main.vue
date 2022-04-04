<template>
    <div>
        <ul v-for='(element, index) in filmList' :key="index">
            <li>{{film.adult}}</li>
            <li>{{film.original_title}}</li>
            <li>{{film.original_language}}</li>
            <li>{{film.vote_average}}</li>
        </ul>
    </div>
</template>

<script>


export default {
    name : 'MainIndex',
    props: ['film'],
    data: function(){
        return {
            filmList : null,
        }
    },
}
</script>

<style scoped lang='scss'>

</style>