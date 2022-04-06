<template>
    <div>
        <ul v-for='(film, index) in filmList' :key="index" >
            <li>{{film.title}}</li>
            <li>{{film.original_title}}</li>
            <li>
                <country-flag :country='flags(film.original_language)' size='big'/>{{film.original_language}}
            </li>
            <li>{{film.vote_average}}</li>
        </ul>
    </div>
</template>

<script>


export default {
    name : 'MainIndex',
    props: ['filmList'],
    methods : {
        flags(name){
            let flag ='';
            if (name === 'en') flag = 'gb';
            else if (name === 'zh') flag = 'cn'
            else if (name === 'ja') flag = 'jp'
            else if (name === 'ko') flag = 'kp'
            else flag = name;
            return flag
        } 
    }
}
</script>

<style scoped lang='scss'>

</style>