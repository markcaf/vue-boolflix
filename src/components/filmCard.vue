<template>
  <div class="col-2">
    <ul class="list-unstyled">
        <li v-if="film.poster_path != null">
            <img :src="`${imageUrl}${film.poster_path}`" :alt="film.title">
        </li>
        <li v-else>
            <img class="placeholder" src="../assets/placeholder.jpg" alt="Immagine non presente">
        </li>
        <li><strong>Titolo:</strong> {{ film.title }}</li>
        <li><strong>Titolo originale:</strong> {{ film.original_title }}</li>
        <li><strong>Media:</strong> {{ film.media_type }}</li>
        <li><strong>Lingua: </strong><lang-flag :iso="film.original_language" /></li>
        <li><strong>Voto:</strong> 
            <i v-for="vote in getIntegerVote(film.vote_average)" :key="vote" class="fa-solid fa-star ms-1 text-warning"></i>
            <span class="ms-1" v-if="film.vote_average == 0">Non disponibile</span>
        </li>
    </ul>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
    name: 'filmCard',
    components: {
        LangFlag,
    },

    data: function(){
        return {
            imageUrl: 'https://image.tmdb.org/t/p/w342'
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
            return Math.round(vote / 2);
        },
    }

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