<template>
	<div id="app">
		<AppHeader
		@correlatedFilms="showFilms"
		@correlatedSeries="showSeries" 
		/>
		<main>
			<MainFilmCards
			:films="filmsArr"
			/>

			<MainSeriesCards
			:series="seriesArr"
			/>
		</main>
	</div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import MainFilmCards from './components/MainFilmCards.vue'
import MainSeriesCards from './components/MainSeriesCards.vue'

export default {
	name: 'App',
		components: {
			AppHeader,
			MainFilmCards,
			MainSeriesCards,
		},
		data() {
			return {
				filmsArr:[],
				seriesArr: [],
			}
		},
		methods: {
			// fill films array with child info
			showFilms(allFilms) {
				this.filmsArr = allFilms;
				// console.log(allFilms)
			},
			// fill series array with child info
			showSeries(allSeries) {
				this.seriesArr = allSeries;
			}
		},
	}
</script>

<style lang="scss">
	:root {
		--clr-neutral-100: #fff;
		--clr-neutral-300: #858585;
		--clr-neutral-500: #434343;
		--clr-neutral-900: #000;
		--clr-txt-primary-500: #D6332B;
	}
	* {
		padding: 0;
		margin: 0;
		box-sizing: border-box;
	}

	html {
		font-size: 20px;
	}

	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
	}
	h2 {
		font-size: 1.2rem;
		& span {
			font-size: 1rem;
		}
	}
	h3 {
		font-size: 1.1rem;
		& span {
			font-size: .8rem;
		}
	}

	h2, h3, p {
		margin: .5em 0;
		color: var(--clr-txt-primary-500);
		max-height: 6ch;
		overflow-y: hidden;
	}
	p {
		font-size: .9rem;
		max-height: 16ch;
		& span {
			font-size: .7rem;
		}
	}

	span {
		display: block;
		color: var(--clr-neutral-100);
	}
	// MAIN RULES
	main {
        padding: 3em 5em;
		background-color: var(--clr-neutral-500);
        height: calc(100vh - 75px);
        overflow-y: auto;
	}
</style>
