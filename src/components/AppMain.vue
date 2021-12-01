<template>
    <main>
        <ul id="cards-container">
            <li class="film-card" v-for="film, i in films" :key="i">
                <a href="#">
                    <h2>{{film.title}}</h2>
                    <h3>{{film.original_title}}</h3>
                    <span>Lingua&colon; {{film.original_language}}</span>
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
    updated() {
        console.log(this.filmsArr)
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
        width: calc(100% / 4 - 2rem);
        min-height: 35ch;
        padding: 1em;
        margin: .5rem 1rem;
        background-color: var(--clr-neutral-900);
        & a {
            color: var(--clr-neutral-100);
            text-decoration: none;
        }
	}
</style>
