<template>
    <section class="mt-3">
        <h1 class="col-2 ps-3 text-white bg-dark">Serie TV</h1>
        <div class="seriesList d-flex flex-wrap">
            <serieCard class="m-3" :serie="serie" v-for="(serie, index) in series" :key="index" />
        </div>
    </section>
</template>

<script>
import serieCard from './serieCard.vue'
export default {
    name: 'seriesList',
    components: {
        serieCard,
    },

    props: {
        'series': {
            required: true,
            type: Array,
        } 
    },

}
</script>

<style>

</style>