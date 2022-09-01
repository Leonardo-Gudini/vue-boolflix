<template>
<main>
    <section>
        <h2>Film</h2>
        <ul>
            
            <li v-for="(film, index) in filmSeriesFound" :key="index">
                <img :src="'https://image.tmdb.org/t/p/w342/' + film.poster_path" alt="cover"/>
                <div class="card-text">
                    <div><span>Titolo: </span>{{film.title}}</div>
                    <div><span>Titolo originale: </span>{{film.original_title}}</div>
                    <country-flag :country='film.original_language' size='medium'/>
                    <div>
                        <span>Voto: </span>
                        <i v-for="n in 5" class="fa-star" :class="(n>getVote(film.vote_average))?'fa-regular':'fa-solid'" :key="n"></i>
                    </div>
                </div>
            </li>
        </ul>
    </section>


    <section>
        <h2>Serie TV</h2>
        <ul>
            <li v-for="(tvSeries, index) in tvSeriesFound" :key="index">
                <img :src="'https://image.tmdb.org/t/p/w342/' + tvSeries.poster_path" alt="cover"/>
                <div class="card-text">
                    <div><span>Titolo: </span>{{tvSeries.name}}</div>
                    <div><span>Titolo originale: </span>{{tvSeries.original_name}}</div>
                    <country-flag :country='tvSeries.original_language' size='medium'/>
                    <div>
                        <span>Voto: </span>
                        <i v-for="n in 5" class="fa-star" :class="(n>getVote(tvSeries.vote_average))?'fa-regular':'fa-solid'" :key="n"></i>
                    </div>
                </div>
            </li>
        </ul>
    </section>
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
    },
    methods:{
        getVote(averageVote){
            return Math.ceil(averageVote / 10 * 5);
        }
    }

}
</script>

<style lang="scss">
    @import '~@fortawesome/fontawesome-free/css/all.css';
    @import "../style/generalStyle.scss";

    main{
        color: white;
        padding: 60px;
        section{
            margin: 40px 0;
            h2{
                font-size: 30px;
                margin-bottom: 20px;
                color: $primary-color;
                border-bottom: 4px solid $bg-color-second;
            }
            ul{
            list-style-type: none;
            display: flex;
            flex-wrap: wrap;
                li{
                    width: calc(100% / 5);
                    height: 500px;
                    background-color: $bg-color-second;
                    .card-text{
                        display: none;
                        div{
                            margin: 10px 0;
                        }
                    }
                    img{
                        width: 100%;
                        height: 100%;
                    }
                }
                li:hover img{
                    display: none;
                }
                li:hover .card-text{
                    display: block;
                    padding: 30px;
                }
            }
        }
        
    }
</style>