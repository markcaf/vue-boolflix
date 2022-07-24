<template>
  <div class="col-2">
    <ul class="list-unstyled text-white">
        <li v-if="serie.poster_path != null">
            <img :src="`${imageUrl}${serie.poster_path}`" :alt="serie.title">
        </li>
        <li v-else>
            <img class="placeholder" src="../assets/placeholder.jpg" alt="Immagine non presente">
        </li>
        <li><strong>Titolo:</strong> {{ serie.name }}</li>
        <li><strong>Titolo originale:</strong> {{ serie.original_name }}</li>
        <li><strong>Media:</strong> {{ serie.media_type }}</li>
        <li v-if="(supportedLanguage.includes(serie.original_language))">
            <strong>Lingua: </strong> <lang-flag :iso="serie.original_language"/>
        </li>
        <li v-else>
            <strong>Lingua: </strong> {{ serie.original_language }}
        </li>
        <li><strong>Voto:</strong>
            <i v-for="vote in getIntegerVote(serie.vote_average)" :key="vote" class="fa-solid fa-star ms-1 text-warning"></i>
            <span class="ms-1" v-if="serie.vote_average == 0">Non disponibile</span>
         </li>
    </ul>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    name: 'serieCard',
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
        }
    },

    props: {
        'serie': {
            required: true,
            type: Object,
        } 
    },

    methods: {
        getIntegerVote(vote){
            return Math.round(vote / 2);
        },
    },

}
</script>

<style lang="scss" scoped>
    img{
        width: 100%;

        &.placeholder{
            cursor: default;
        }
    }

</style>