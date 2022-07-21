<template>
  <div id="app">
    <Header @search="search" />
    <Main 
    :films="filmsList" 
    :TvSeries="TvSeriesList" />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from 'axios'

export default {
  name: 'App',
  data() {
    return {
      apiFilmUrl: "https://api.themoviedb.org/3/search/movie?api_key=86f90d02335fe15299eb1c2d6f51cae6&language=it-IT&query=",
      apiTvSeriesUrl: "https://api.themoviedb.org/3/search/tv?api_key=86f90d02335fe15299eb1c2d6f51cae6&language=it-IT&query=",
      filmsList: [],
      TvSeriesList: [],
    }
  },
  components: {
      Header,
      Main,
    },
  methods: {
    search(search) {
      
      axios.get(this.apiFilmUrl + search)
        .then(response => {
          this.filmsList = response.data.results
        })

      axios.get(this.apiTvSeriesUrl + search)
        .then(response => {
          this.TvSeriesList = response.data.results
        })
      }
    },
  }
</script>

<style lang="scss" scoped>
@import '~bootstrap/scss/bootstrap.scss';
@import './styles/general.scss';

  div {
    background-color: #f5f5f5;
  }
</style>
