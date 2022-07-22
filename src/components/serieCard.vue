<template>
  <div class="col-2">
    <ul class="list-unstyled">
        <li v-if="serie.poster_path != null">
            <img :src="`${imageUrl}${serie.poster_path}`" :alt="serie.title">
        </li>
        <li v-else>
            <img class="placeholder" src="../assets/placeholder.jpg" alt="Immagine non presente">
        </li>
        <li><strong>Titolo:</strong> {{ serie.name }}</li>
        <li><strong>Titolo originale:</strong> {{ serie.original_name }}</li>
        <li><strong>Media:</strong> {{ serie.media_type }}</li>
        <li><strong>Lingua: </strong><lang-flag :iso="serie.original_language" /></li>
        <li><strong>Voto:</strong> {{ serie.vote_average }}</li>
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
            imageUrl: 'https://image.tmdb.org/t/p/w342'
        }
    },

    props: {
        'serie': {
            required: true,
            type: Object,
        } 
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