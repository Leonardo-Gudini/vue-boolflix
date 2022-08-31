<template>
  <div id="app">
    <MyHeader @search="searchFilmSeries"/>
    <MyMain :filmSeriesFound="filmSeriesFound"/>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue';
import MyMain from './components/MyMain.vue';
import axios from "axios";

export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain
  },
  data(){
    return{
      filmSeriesFound: [],
    }
  },
  methods: {
    searchFilmSeries(searchText){
      axios.get("https://api.themoviedb.org/3/search/movie?api_key=62496f666966773e2ed0aa3c4d10d49c&query=" + searchText + "&language=it-IT")
        .then( res => {
            this.filmSeriesFound = res.data.results;
            console.log(this.filmSeriesFound)
        })
    }
  }

}
</script>

<style lang="scss">
  @import "style/generalStyle.scss"
</style>
