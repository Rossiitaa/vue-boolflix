<template>
    <main>
    
        <section>
            <h2>Film:</h2>
            <ul class="position-relative" v-for="film in films" :key="film.id">
                <div>
                    <img :src="cover(film.poster_path)" alt="">
                </div>
                <div  class="cont-text">
                    <li>Title: {{ film.title }}</li>
                    <li>Original Title: {{ film.original_title }}</li>
                    <li>
                        Language: <img class="img-lang-size" :src="flagUrl(film.original_language)" alt="">
                    </li>
                    <li>
                        Vote: <i v-for="vote in voteAverage(film.vote_average)" :key="vote" class="fa-solid fa-star"></i>
                    </li>
                    <li>Overview: {{ film.overview }}</li>
                </div>
            </ul>
        </section>


        <section>
            <h2>Tv Series:</h2>
            <ul class="position-relative" v-for="series in tvSeries" :key="series.id">
                <div>
                    <img :src="cover(series.poster_path)" alt="">
                </div>
                <div class="cont-text">
                    <li>Title: {{ series.name }}</li>
                    <li>Original Title: {{ series.original_name }}</li>
                    <li>
                        Language: <img class="img-lang-size" :src="flagUrl(series.original_language)" alt="">
                    </li>
                    <li>
                        Vote: <i v-for="vote in voteAverage(series.vote_average)" :key="vote" class="fa-solid fa-star">
                        </i> 
                    </li>
                    <li>Overview: {{ series.overview }}</li>
                </div>
            </ul>
        </section>
            
        
    </main>
</template>

<script>
export default {
name: 'Main',    
    data() {
        return {
            hover: false,
        }
    },

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
@import '~bootstrap/scss/bootstrap.scss';
    hr {
        width: 423vw;
    }


    h2 {
        color: #fff;
        width: 130px;
        height: 100px;
        padding-right: 4rem;
        text-align: center;
    }

    img {
        width: 100%;
        padding: 0.5rem;
    }

    section {
        display: flex;
        align-items: center;
        overflow: auto;

    ul {
        list-style: none;
        color: #fff;
        padding: 0;

            &:hover .cont-text {
            visibility: visible;
            }
    }
    li {
        padding: 0.5rem;
    }
    .img-lang-size {
        width: 30px;
    }
    svg {
        color: #ffbe45;
    }
    div > img {
        width: 25rem;
        height: 35rem;
    }
    .cont-text {
        width: 96.2%;
        height: 97.2%;
        position: absolute;
        top: 8px;
        left: 8px;
        background-color: #000;
        visibility: hidden;
    }
}
    

</style>