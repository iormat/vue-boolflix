<template>
    <section id="films">
        <h2>Correlated Films</h2>
        <ul class="cards-container">
            <li class="card film-card" v-for="film, i in films" :key="i">
                <img class="card_image" :src='checkImage(film)' :alt="film.title">
                <div class="card_info">
                    <h2>Titolo&colon; <span>{{film.title}}</span></h2>
                    <h3> Titolo Originale&colon; <span>{{film.original_title}}</span></h3>
                    <p>Overview&colon; <span>{{film.overview}}</span></p>
                    <div class="more-info">
                        <span class="evaluation"> Voto&colon; 
                            <StarRating
                            :rating="getRating(film)"
                            v-model="rating"
                            :read-only="true"
                            :star-size="20"
                            :show-rating="false"
                            :max-rating="5"
                            /> 
                        </span>
                        <span>
                            <img :src="checkFlag(film)" :alt="film.original_language">
                        </span>
                    </div>
                </div>
            </li>
        </ul>
    </section>
</template>

<script>
import StarRating from 'vue-star-rating';
export default {
    name: 'MainFilmCards',
    components: {
        StarRating,
    },
    props: {
        films: Array,
    },

    methods: {
        checkFlag(film) {
            if(film.original_language === 'en') {
                return require("../assets/en-flag.png")
            }else if(film.original_language === 'it') {
                return require("../assets/it-flag.png")
            }
        },
        checkImage(film) {
            if(film.poster_path === null) {
                return "https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.salonlfc.com%2Fwp-content%2Fuploads%2F2018%2F01%2Fimage-not-found-1-scaled-1150x647.png&f=1&nofb=1"
            }else {
                return "https://image.tmdb.org/t/p/w342" + film.poster_path;
            }
        },
        getRating(film) {
            this.rating = Math.round(parseFloat(film.vote_average / 2))
        },

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