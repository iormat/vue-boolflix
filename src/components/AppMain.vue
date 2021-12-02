<template>
    <main>
        <ul id="cards-container">
            <li class="film-card" v-for="film, i in films" :key="i">
                <a href="#">
                    <img class="film-card_image" :src= '"https://image.tmdb.org/t/p/w342" + film.poster_path' :alt="film.title">
                    <div class="film-card_info">
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
    </main>
</template>

<script>
export default {
    name: 'AppMain',
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
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
	main {
        padding: 3em 5em;
		background-color: var(--clr-neutral-500);
        height: calc(100vh - 75px);
        overflow-y: auto;
	}
    #card-container {
        width: 70%;
        margin: 0 auto;
    }
    .film-card {
        display: inline-block;
        vertical-align: text-top;
        width: calc(100% / 4 - 1.5rem);
        min-height: 40ch;
        padding: .25em 0;
        margin: .75rem .75rem;
        background-color: var(--clr-neutral-900);
        position: relative;
        overflow-y: auto;
        &:hover .film-card_image {
            display: none;
        }
        & a {
            color: var(--clr-neutral-100);
            text-decoration: none;
        }
        & .film-card_image {
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
    .film-card_info {
        padding: 0 1em;
        & span img {
            margin-top: .5rem;
            position: initial;
            width: 14%;
        }   
    }
</style>