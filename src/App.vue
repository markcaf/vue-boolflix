<template>
  <div id="app">
    <Header @search="search"/>
    <Main :films="films" :series="series" :message="message"/>
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
      message: 'Benvenuto nel programma di ricerca per Film e Serie Tv, inserisci il film/serie nel campo di input per iniziare.',
      apiKey: '59c53a96f763c9716248c35c07d50ee0',
      apiUrl: 'https://api.themoviedb.org/3/search/multi',
    };
  },

  methods: {
    getAllMedia(apiParams){
      this.films = [];
      this.series = [];
      axios.get(this.apiUrl, apiParams)
      .then( (result) => {
        this.listAll = result.data.results;

        this.listAll.forEach(element => {
          if (element.media_type == 'movie'){
            this.films.push(element);
          } else if (element.media_type == 'tv') {
            this.series.push(element);
            };
          });
        
        this.message = 'La tua ricerca non ha prodotto risultati.'

      })

      .catch((error) => {
        console.warn(error);
      })
    },

    search(searchInput){
      const apiParams = 
      { 
        params: {
          api_key: this.apiKey,
          language: 'it-IT',
          query: searchInput,
        }
      }
      this.getAllMedia(apiParams);
    }
  },
}
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body{
  background-color: #1b1b1b;
}

::-webkit-scrollbar {
  height: 5px;
  width: 5px;
}

::-webkit-scrollbar-track {
  background: #282828;
}

::-webkit-scrollbar-thumb {
  background: #707070;
}

::-webkit-scrollbar-thumb:hover {
  background: #474747;
}
</style>
