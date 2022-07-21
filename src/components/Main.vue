<template>
    <main>
        <ul v-for="film in films" :key="film.id">
            <li>Title: {{ film.title }}</li>
            <li>Original Title: {{ film.original_title }}</li>
            <li>
                Language: <img class="img-size" :src="flagUrl(film.original_language)" alt="">
                </li>
            <li>Vote: {{ film.vote_average }}</li>
        </ul>

        <ul v-for="series in TvSeries" :key="series.id">
            <li>Title: {{ series.name }}</li>
            <li>Original Title: {{ series.original_name }}</li>
            <li>
                Language: <img class="img-size" :src="flagUrl(series.original_language)" alt="">
                </li>
            <li>Vote: {{ series.vote_count }}</li>
        </ul>
    </main>
</template>

<script>
export default {
name: 'Main',    

    props: {
        films: {
            type: Array,
        },
        TvSeries: {
            type: Array,
        },
    },
    methods: {
        flagUrl(language) {
            return `https://www.unknown.nu/flags/images/${language}-100`
        },
    }
}
</script>

<style lang="scss" scoped>
ul {
    list-style: none;
    padding: 10px;
}
.img-size {
    width: 30px;
}
</style>