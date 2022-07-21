<template>
  <div class="filmList d-flex flex-wrap justify-content-center">
    <filmCard class="m-4" :film="film" v-for="(film, index) in films" :key="index" />
  </div>
</template>

<script>
import filmCard from './filmCard.vue'
export default {
    name: 'filmsList',
    components: {
        filmCard,
    },

    props: {
        'films': {
            required: true,
            type: Array,
        } 
    },

}
</script>

<style>

</style>