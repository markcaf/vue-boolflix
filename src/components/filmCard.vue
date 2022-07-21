<template>
  <div class="col-2">
    <ul>
        <li><strong>Titolo:</strong> {{ film.title }}</li>
        <li><strong>Titolo originale:</strong> {{ film.original_title }}</li>
        <li><strong>Lingua:</strong> {{ film.original_language }}</li>
        <li><strong>Voto:</strong> {{ film.vote_average }}</li>
    </ul>
  </div>
</template>

<script>
export default {
    name: 'filmCard',

    props: {
        'film': {
            required: true,
            type: Object,
        } 
    },

}
</script>

<style>

</style>