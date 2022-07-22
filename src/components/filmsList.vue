<template>
    <section class="mt-3">
        <h1 class="col-2 ps-3 text-white bg-dark">Film</h1>
        <div class="filmList d-flex flex-wrap">
            <filmCard class="m-3" :film="film" v-for="(film, index) in films" :key="index" />
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

<style>

</style>