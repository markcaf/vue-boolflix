<template>
  <div class="filmList">
    <filmCard v-for="(film, index) in films" :key="index" />
  </div>
</template>

<script>
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