<template>
  <div id="app">
    <Header @search="getAllMedia"/>
    <Main :films="films" :series="series"/>
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
      series: [],
      listAll: [],
      apiKey: '59c53a96f763c9716248c35c07d50ee0',
      apiUrl: 'https://api.themoviedb.org/3/search/multi',
    };
  },

  methods: {
    getAllMedia(search){
      this.films = [];
      this.series = [];
      axios.get(`${this.apiUrl}?api_key=${this.apiKey}&language=it-IT&query=${search}`)
      .then( (result) => {
        console.log(result.data.results);
        this.listAll = result.data.results;

        this.listAll.forEach(element => {
          if (element.media_type == 'movie'){
            this.films.push(element);
          } else if (element.media_type == 'tv') {
            this.series.push(element);
            };          
        });

        console.log(this.films);
        console.log(this.series);
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

  background-color: #1b1b1b;

  /* width */
  ::-webkit-scrollbar {
    height: 5px;
  }
  
  /* Track */
  ::-webkit-scrollbar-track {
    background: #282828;
  }
  
  /* Handle */
  ::-webkit-scrollbar-thumb {
    background: #707070;
  }
  
  /* Handle on hover */
  ::-webkit-scrollbar-thumb:hover {
    background: #101010;
  }
}
</style>
