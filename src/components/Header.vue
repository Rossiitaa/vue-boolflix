<template>
    <header>
        <div>
            <input type="text" placeholder="Inserisci Nome Film/Serie Tv" v-model.trim="filmSearch" @keyup.enter="$emit('search' , filmSearch)">
            <button @click="$emit('search' , filmSearch)">Search</button>
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
        margin-right: 14px;
        padding-right: 5px;
    }

    div {
        padding : 10px;
    }
</style>