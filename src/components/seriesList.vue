<template>
    <section class="mt-5 mb-5">
        <h1 class="col-2 text-white">Serie TV</h1>
        <div class="seriesList d-flex px-3">
            <serieCard class="mt-3 mb-5" :serie="serie" v-for="serie in series" :key="serie.id" />
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