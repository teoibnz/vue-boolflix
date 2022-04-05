<template>
    <div>
        <ul v-for='(film, index) in filmList' :key="index" >
            <li>{{film.title}}</li>
            <li>{{film.original_title}}</li>
            <li>{{film.original_language}}</li>
            <li>{{film.vote_average}}</li>
        </ul>
    </div>
</template>

<script>


export default {
    name : 'MainIndex',
    props: ['filmList'],
    
}
</script>

<style scoped lang='scss'>

</style>