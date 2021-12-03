<template>
    <section id="series">
        <h2>correlated series</h2>
        <ul class="cards-container">
            <li class="card serie-card" v-for="serie, i in series" :key="i">
                <img class="card_image" :src='checkImage(serie)' :alt="serie.title">
                <div class="card_info">
                    <h2>Titolo&colon; <span>{{serie.name}}</span></h2>
                    <h3> Titolo Originale&colon; <span>{{serie.original_name}}</span></h3>
                    <p>Overview&colon; <span>{{serie.overview}}</span></p>
                    <div class="more-info">
                        <span class="evaluation"> Voto&colon; 
                            <StarRating
                            v-model="rating"
                            :rating="getRating(serie)"
                            :read-only="true"
                            :star-size="20"
                            :show-rating="false"
                            :max-rating="5"
                            /> 
                        </span>
                        <span>
                            <img :src="checkFlag(serie)" :alt="serie.original_language">
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
    name: 'MainSeriesCards',
    components: {
        StarRating,
    },

    props: {
        series: Array,
    },
    methods: {
        checkFlag(serie) {
            if(serie.original_language === 'en') {
                return require("../assets/en-flag.png")
            }else if(serie.original_language === 'it') {
                return require("../assets/it-flag.png")
            }
        },
        checkImage(serie) {
            if(serie.poster_path === null) {
                return "https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.salonlfc.com%2Fwp-content%2Fuploads%2F2018%2F01%2Fimage-not-found-1-scaled-1150x647.png&f=1&nofb=1"
            }else {
                return "https://image.tmdb.org/t/p/w342" + serie.poster_path;
            }
        },
        getRating(serie){
            this.rating = Math.round(parseFloat(serie.vote_average / 2))
        },
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    #series > h2 {
        padding: 1rem 0;
        font-size: 2rem;
        text-transform: uppercase;
    }
</style>