<template>
  <div id="app">
    <Header @search="search" />
    <Main :films="filmsList" />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data() {
    return {
      apiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=86f90d02335fe15299eb1c2d6f51cae6&language=it-IT&query=',
      filmsList: [],
    }
  },
  methods: {
    search: function(search) {
      axios.get(`${this.apiUrl}${search}`)
        .then((response) => {
          this.filmsList = response.data.results
        })
      },
    },
    created() {
      this.search();
    },
  }
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss';
@import './styles/general.scss';

</style>
