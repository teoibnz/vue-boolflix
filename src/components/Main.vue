<template>
    <div >
        <FilmContainer v-for='(element, index) in filmList' :key="index" :film='element'/>
    </div>
</template>

<script>
import FilmContainer from './FilmContainer.vue'


export default {
    name : 'MainIndex',
    props: ['film'],
    components : {
        FilmContainer
    },
}
</script>

<style scoped lang='scss'>

</style>