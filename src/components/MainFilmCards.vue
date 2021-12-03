<template>
    <section id="films">
        <h2>Correlated Films</h2>
        <ul class="cards-container">
            <li class="card film-card" v-for="film, i in films" :key="i">
                <a href="#">
                    <img class="card_image" :src= '"https://image.tmdb.org/t/p/w342" + film.poster_path' :alt="film.title">
                    <div class="card_info">
                        <h2>Titolo&colon; <span>{{film.title}}</span></h2>
                        <h3> Titolo Originale&colon; <span>{{film.original_title}}</span></h3>
                        <p>Overview&colon; <span>{{film.overview}}</span></p>
                        <div class="more-info">
                            <span class="evaluation"> Voto&colon; {{film.vote_average}} </span>
                            <span>
                                <img :src="checkFlag(film)" :alt="film.original_language">
                            </span>
                        </div>
                    </div>
                </a>
            </li>
        </ul>
    </section>
</template>

<script>
export default {
    name: 'MainFilmCards',
    data() {
        return {

        }
    },

    props: {
        films: Array,
    },

    methods: {
        checkFlag(film) {
            if(film.original_language === 'en') {
                return "../assets/en-flag.png"
            }else if(film.original_language === 'it') {
                return "../assets/it-flag.df0c0856.png"
            }
        }
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    #films > h2 {
        font-size: 2rem;
        text-transform: uppercase;
    }
</style>