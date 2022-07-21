<template>
    <header>
        <div>
            <input type="text" placeholder="Inserisci Nome Film/Serie Tv" v-model.trim="filmSearch" @keyup.enter="$emit('Search' , filmSearch)">
            <button @click="$emit('Search' , filmSearch)">Search</button>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            filmSearch: '',
        }
    },
}
</script>

<style lang="scss" scoped>
    input {
        margin: 10px;
    }
</style>