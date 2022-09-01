<template>
  <div id="app">
    <MyHeader @search="searchFilmSeries"/>
    <MyMain :filmSeriesFound="filmSeriesFound" :tvSeriesFound="tvSeriesFound"/>
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
      tvSeriesFound : [],
    }
  },
  methods: {
    searchFilmSeries(searchText){
      axios.all([
        axios.get("https://api.themoviedb.org/3/search/movie?api_key=62496f666966773e2ed0aa3c4d10d49c&query=" + searchText + "&language=it-IT"),
        axios.get("https://api.themoviedb.org/3/search/tv?api_key=62496f666966773e2ed0aa3c4d10d49c&query=" + searchText + "&language=it-IT")
      ])
      .then(axios.spread( (filmRes, tvSeriesRes) => {
        this.filmSeriesFound = filmRes.data.results;
        this.tvSeriesFound = tvSeriesRes.data.results;
      }))
    }
  }
}
</script>

<style lang="scss">
  @import "style/generalStyle.scss"
</style>
