<template>
    <main>
        <ul v-for="film in films" :key="film.id">
            <img :src="cover(film.poster_path)" alt="">
            <li>Title: {{ film.title }}</li>
            <li>Original Title: {{ film.original_title }}</li>
            <li>
                Language: <img class="img-size" :src="flagUrl(film.original_language)" alt="">
                </li>
            <li>
                Vote: <i v-for="vote in voteAverage(film.vote_average)" :key="vote" class="fa-solid fa-star"></i>
            </li>
        </ul>

        <ul v-for="series in tvSeries" :key="series.id">
            <img :src="cover(series.poster_path)" alt="">
            <li>Title: {{ series.name }}</li>
            <li>Original Title: {{ series.original_name }}</li>
            <li>
                Language: <img class="img-size" :src="flagUrl(series.original_language)" alt="">
            </li>
            <li>
                Vote: <i v-for="vote in voteAverage(series.vote_count)" :key="vote" class="fa-solid fa-star"></i> 
            </li>
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
        tvSeries: {
            type: Array,
        },
    },
    methods: {
        flagUrl(language) {
            return `https://www.unknown.nu/flags/images/${language}-100`
        },
        cover(poster_path) {
            return `https://image.tmdb.org/t/p/w342${poster_path}`
        },
        voteAverage(vote) {
            return Math.ceil(vote / 2)
        }
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