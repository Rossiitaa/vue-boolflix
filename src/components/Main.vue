<template>
    <main>
        <ul v-for="film in films" :key="film.id">
            <li>Title: {{ film.title }}</li>
            <li>Original Title: {{ film.original_title }}</li>
            <li>Language: {{ film.original_language }}</li>
            <li>Vote: {{ film.vote_average }}</li>
        </ul>
    </main>
</template>

<script>
export default {
name: 'Main',
    props: {
        films: {
            type: Array,
            required: true,
        },
    },
}
</script>

<style lang="scss" scoped>
ul {
    list-style: none;
    padding: 10px;
}
</style>