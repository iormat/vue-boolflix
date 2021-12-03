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
// GENERAL INITIAL SETUP
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
// TEXT GENERAL DETAILS
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
		// general cards style
		.card {
			display: inline-block;
			vertical-align: text-top;
			width: calc(100% / 4 - 1.5rem);
			min-height: 45ch;
			padding: .25em .5em;
			margin: .75rem .75rem;
			background-color: var(--clr-neutral-900);
			position: relative;
			overflow-y: auto;
			&:hover .card_image {
				display: none;
			}
			& .card_image {
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
			& span img {
				width: 15%;
			}
		}
	}

</style>