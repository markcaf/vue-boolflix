<template>
    <section class="mt-5 mb-5">
        <h1 class="col-2 ps-3 text-white">Serie TV</h1>
        <div class="seriesList d-flex">
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

<style lang="scss" scoped>
    .seriesList{
        overflow: auto;
    }

</style>