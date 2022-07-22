<template>
  <div class="col-2">
    <ul>
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

    props: {
        'serie': {
            required: true,
            type: Object,
        } 
    },

}
</script>

<style>

</style>