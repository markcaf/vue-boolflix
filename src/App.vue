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
      apiKey: '59c53a96f763c9716248c35c07d50ee0',
      apiUrl: 'https://api.themoviedb.org/3/search/movie',
    };
  },

  methods: {
    getFilms(search){
      axios.get(`${this.apiUrl}?api_key=${this.apiKey}&language=it-IT&query=${search}`)
      .then( (result) => {
        console.log(result.data.results);
        this.films = result.data.results;
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
