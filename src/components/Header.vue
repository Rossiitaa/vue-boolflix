<template>
    <header class="d-flex justify-content-between align-items-center">
        <div>
            <h2>
                BOOLFLIX
            </h2>
        </div>
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
@import '~bootstrap/scss/bootstrap.scss';

header {
        background-color: #000;
        padding: 1rem 2rem;
    h2 {
        color: #ed0001;
    }
    input {
        margin-right: 14px;
        padding-right: 5px;
    }
}
</style>