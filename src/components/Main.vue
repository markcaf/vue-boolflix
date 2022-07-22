<template>
  <main class="py-3">
    <div class="container">
        <div class="row">
            <div class="col">
                <filmsList :films="films" />
            </div>
        </div>

        <div class="row">
            <div class="col">
                <seriesList :series="series" />
            </div>
        </div>
    </div>
  </main>
</template>

<script>
import filmsList from './filmsList.vue'
import seriesList from './seriesList.vue'

export default {
    name: 'Main',
    components: {
        filmsList,
        seriesList,
    },

    props: {
        'films': {
            required: true,
            type: Array,
        },
        
        'series': {
            required: true,
            type: Array,
        },
    },

}
</script>

<style>

</style>