<template>
<main>
    <div>
        <h2>Film</h2>
        <ul>
            
            <li v-for="(film, index) in filmSeriesFound" :key="index">
                <img :src="'https://image.tmdb.org/t/p/w342/' + film.poster_path" alt="cover"/>
                <div><span>Titolo: </span>{{film.title}}</div>
                <div><span>Titolo originale: </span>{{film.original_title}}</div>
                <country-flag :country='film.original_language' size='medium'/>
                <div><span>Voto: </span>{{film.vote_average}}</div>
            </li>
        </ul>
    </div>


    <div>
        <h2>Serie TV</h2>
        <ul>
            <li v-for="(tvSeries, index) in tvSeriesFound" :key="index">
                <img :src="'https://image.tmdb.org/t/p/w342/' + tvSeries.poster_path" alt="cover"/>
                <div><span>Titolo: </span>{{tvSeries.name}}</div>
                <div><span>Titolo originale: </span>{{tvSeries.original_name}}</div>
                <country-flag :country='tvSeries.original_language' size='medium'/>
                <div><span>Voto: </span>{{tvSeries.vote_average}}</div>
            </li>
        </ul>
    </div>
</main>
</template>

<script>
import CountryFlag from 'vue-country-flag'

export default {
    name: "MyMain",
    props:{
        filmSeriesFound: Array,
        tvSeriesFound: Array,
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