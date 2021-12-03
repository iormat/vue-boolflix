<template>
    <section id="series">
        <h2>correlated series</h2>
        <ul class="cards-container">
            <li class="card serie-card" v-for="serie, i in series" :key="i">
                <a href="#">
                    <img class="card_image" :src= '"https://image.tmdb.org/t/p/w342" + serie.poster_path' :alt="serie.title">
                    <div class="card_info">
                        <h2>Titolo&colon; <span>{{serie.title}}</span></h2>
                        <h3> Titolo Originale&colon; <span>{{serie.original_title}}</span></h3>
                        <p>Overview&colon; <span>{{serie.overview}}</span></p>
                        <div class="more-info">
                            <span class="evaluation"> Voto&colon; {{serie.vote_average}} </span>
                            <span>
                                <img :src="checkFlag(serie)" :alt="serie.original_language">
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
    name: 'MainSeriesCards',
    provide() {
        return {
            seriesArr: [],
        }
    },

    props: {
        series: Array,
    },

    methods: {
        checkFlag(serie) {
            if(serie.original_language === 'en') {
                return "../assets/en-flag.png"
            }else if(serie.original_language === 'it') {
                return "../assets/it-flag.df0c0856.png"
            }
        }
    }
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