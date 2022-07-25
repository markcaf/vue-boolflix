<template>
    <section class="mt-3 mb-5">
        <h1 class="col-2 text-white">Film</h1>
        <div class="filmList d-flex px-3">
            <filmCard class="mt-3 mb-5" :film="film" v-for="film in films" :key="film.id" />
        </div>
    </section>
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

<style lang="scss" scoped>
    .filmList{
        overflow: auto;
    }

</style>