<template>
  <header>
    <div class="container-fluid p-4 border">
        <div class="row justify-content-between">
            <div class="col-6 logo">
                <h3>Boolflix</h3>
            </div>

            <div class="col-4">
                <div class="input-group">
                    <input v-model.trim="searchInput" @keyup.enter="$emit('search', searchInput)"
                    type="text" class="form-control" placeholder="Inserisci il titolo di un film" aria-label="films" aria-describedby="basic-addon1">
                    <span @click.prevent="$emit('search', searchInput)" class="input-group-text" id="basic-addon1">Cerca</span>
                </div>
            </div>
        </div>
    </div>
  </header>
</template>

<script>
export default {
    name: 'Header',

    data: function(){
        return {
            searchInput: '',
        }
    }
}
</script>

<style lang="scss" scoped>
    .input-group{
        span{
            cursor: pointer;
        }
    }

</style>