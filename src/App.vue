<template>
  <div id="app">
    <Header @search="getFilms"/>
    <Main :films="films" />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },

  data: function(){
    return {
      films: [],
      apiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=59c53a96f763c9716248c35c07d50ee0&language=it-IT&query=',
    };
  },

  methods: {
    getFilms: function(search){
      console.log("Questo è search: " + search)
      this.apiUrl = this.apiUrl + search;
      console.log("Questo è apiUrl con la query data da search: " + this.apiUrl);
      axios.get(this.apiUrl)
      .then( (result) => {
        this.films = result.data.results;
        console.log("Array generato con i risultati della query: " + this.films);
        this.apiUrl = 'https://api.themoviedb.org/3/search/movie?api_key=59c53a96f763c9716248c35c07d50ee0&language=it-IT&query=';
        console.log("apiUrl ripristinato senza parole chiave nella query: " + this.apiUrl);
      })

      .catch((error) => {
        console.warn(error);
      })
    }
  },

  created(){
  
  }
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
