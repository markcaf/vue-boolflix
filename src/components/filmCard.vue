<template>
  <div class="col-2">
    <div class="film-card">
        <img v-if="film.poster_path != null" :src="`${imageUrl}${film.poster_path}`" :alt="film.title">
        <img v-else class="placeholder" src="../assets/placeholder.jpg" alt="Immagine non presente">
    
        <ul class="list-unstyled text-white">
            <li><strong>Titolo:</strong> {{ film.title }}</li>
            <li v-if="film.title != film.original_title">
                <strong>Titolo originale:</strong> {{ film.original_title }}
            </li>
            <li v-if="(supportedLanguage.includes(film.original_language))">
                <strong>Lingua: </strong> <lang-flag :iso="film.original_language"/>
            </li>
            <li v-else>
                <strong>Lingua: </strong> {{ film.original_language }}
            </li>
            <li><strong>Voto: </strong> 
                <span v-if="film.vote_average == 0">Non disponibile</span>

                <i v-else v-for="n in 5" :key="n" class="fa-star text-warning"
                   :class="n <= getIntegerVote(film.vote_average) ? 'fas' : 'far'"></i>
            </li>
            <li v-if="film.overview != ''" ><strong>Trama:</strong> {{ film.overview }}</li>
            <li v-else ><strong>Trama:</strong> Nessuna informazione disponibile</li>
            <div class="text-center">
                <button @click="castSearch(film.id)" class="my-2 btn btn-outline-danger">Scopri il cast</button>
                <li v-for="member in cast" :key="member.id" class="mt-2"> 
                    {{member.name}} 
                </li>
            </div>
        </ul>
    </div>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
import axios from 'axios';

export default {
    name: 'filmCard',
    components: {
        LangFlag,
    },

    data: function(){
        return {
            imageUrl: 'https://image.tmdb.org/t/p/w342',

            supportedLanguage: [
                'am', 'az', 'be', 'bn', 'bg', 'zh', 'ca', 'cs', 'en', 'et', 'fr', 'de', 'ha', 'hi', 'hu', 'it', 'ja', 'jv', 
                'km', 'ko', 'lv', 'ms', 'mr', 'fa', 'pl', 'pt', 'ro', 'ru', 'es', 'sw', 'ta', 'te', 'th', 'tr', 'uz', 'vi'
            ],

            apiUrl: 'https://api.themoviedb.org/3/movie/',
            apiKey: '59c53a96f763c9716248c35c07d50ee0',
            cast: [],
        }
    },

    props: {
        'film': {
            required: true,
            type: Object,
        },
    },

    methods: {
        getIntegerVote(vote){
            return Math.ceil(vote / 2);
        },

        castSearch(id){
            const apiParams = 
            { 
                params: {
                api_key: this.apiKey,
                language: 'it-IT',
                }
            }
            this.getCast(apiParams);
        },

        getCast(apiParams){
            axios.get(this.apiUrl + this.film.id + '/credits?', apiParams)
            .then( (result) => {
                this.cast = result.data.cast;
                this.cast.splice(5);
                console.log(this.cast);
            })

            .catch((error) => {
                console.warn(error);
            })
        },

    }

}
</script>

<style lang="scss" scoped>
    .film-card{
        height: 320px;
        border: 1px black solid;

        &:hover{
            transform: scale(1.1);
            transition: transform 0.7s;

            img{
                display: none;
            }

            ul{
                display: block;
            }
        }

        img{
            display: block;
            width: 100%;
            height: 320px;

            &.placeholder{
                cursor: default;
            }
        }

        ul{
            display: none;
            padding: 20px;
            background-color: #010101;
            height: 320px;
            border: 1px solid white;
            overflow: auto;
            font-size: 14px;
            scrollbar-width: 1px;

            li {
                margin-bottom: 10px;
            }
        }

    }
</style>