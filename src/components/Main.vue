<template>
  <main>
    <div class="container">
        <div class="row">
            <div class="col">
                <filmsList :films="films" />
            </div>
        </div>
    </div>
  </main>
</template>

<script>
import filmsList from './filmsList.vue'

export default {
    name: 'Main',
    components: {
        filmsList,
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