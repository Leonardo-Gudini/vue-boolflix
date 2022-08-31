<template>
<main>
    <ul>
        <li v-for="(film, index) in filmSeriesFound" :key="index">
            <div>{{film.title}}</div>
            <div>{{film.original_title}}</div>
            <country-flag :country='film.original_language' size='medium'/>
            <div>{{film.vote_average}}</div>
        </li>
    </ul>
</main>
</template>

<script>
import CountryFlag from 'vue-country-flag'

export default {
    name: "MyMain",
    props:{
        filmSeriesFound: Array,
    },
    components:{
        CountryFlag
    }

}
</script>

<style lang="scss">
    @import "../style/generalStyle.scss";

    main{
        color: white;
        padding: 60px;
        ul{
            list-style-type: none;
            display: flex;
            li{
                margin: 20px;
                padding: 40px;
                background-color: $bg-color-second;
            }
        }
    }
</style>