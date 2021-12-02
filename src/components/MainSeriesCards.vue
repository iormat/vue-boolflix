<template>
    <section id="series">
        <h2>correlated series</h2>
        <ul id="serie-cards-container">
            <li class="serie-card" v-for="serie, i in series" :key="i">
                <a href="#">
                    <img class="serie-card_image" :src= '"https://image.tmdb.org/t/p/w342" + serie.poster_path' :alt="serie.title">
                    <div class="serie-card_info">
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

    #serie-card-container {
        width: 70%;
        margin: 0 auto;
    }
    .serie-card {
        display: inline-block;
        vertical-align: text-top;
        width: calc(100% / 4 - 1.5rem);
        min-height: 40ch;
        padding: .25em 0;
        margin: .75rem .75rem;
        background-color: var(--clr-neutral-900);
        position: relative;
        overflow-y: auto;
        &:hover .serie-card_image {
            display: none;
        }
        & a {
            color: var(--clr-neutral-100);
            text-decoration: none;
        }
        & .serie-card_image {
            display: block;
            width: 100%;
            height: 100%;
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            z-index: 1;
        }
	}
    .serie-card_info {
        padding: 0 1em;
        & span img {
            margin-top: .5rem;
            position: initial;
            width: 14%;
        }   
    }
</style>