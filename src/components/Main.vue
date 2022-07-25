<template>
  <main class="py-3">
    <div class="container">
        <div class="row">
            <div class="col">
                <filmsList :films="films" v-if="films.length"/>
                <!-- <h5 class="text-white" v-else>Nessun risultato trovato per la tua ricerca.</h5> -->
            </div>
        </div>

        <div class="row">
            <div class="col">
                <seriesList :series="series" v-if="series.length"/>
            </div>
        </div>

        <h1 class="text-white text-center mt-5" v-if="series.length===0 && films.length===0">
            {{this.message}}
        </h1>
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

        'message': {
            required: true,
            type: String,
        }
    },

}
</script>

<style>

</style>