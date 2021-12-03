<template>
	<header>
		<h1> BoolFlix </h1>
		<div>
			<label for="input-search">
				<input id="input-search" type="text" v-model.trim="userInput" @keyup.enter="checkSeriesFilms">
			</label>
			<button @click.prevent="checkSeriesFilms"> Search </button>
		</div>
	</header>
</template>

<script>
import axios from "axios";
export default {	
	name: 'AppHeader',
	data () {
		return {
			seriesArr: [],
			filmsArr: [],
			userInput: "",
			userResearch: "",
		}
	},
	methods: {
		// start films search
		saveUserSearchFilms() {
			this.userResearch = this.userInput;
			let apiObj = "https://api.themoviedb.org/3/search/movie?api_key=44637956b9084a5c4eb306d80e3f63ea&query=" + this.userResearch
			axios
			.get(apiObj)
			.then((obj) => {
				this.filmsArr = obj.data.results;
				// // used to send films Array info to parent(App)
				this.$emit('correlatedFilms', this.filmsArr)
			})
		},
		// start series search
		saveUserSearchSeries() {
			this.userResearch = this.userInput;
			this.userInput = "";
			let apiObj = "https://api.themoviedb.org/3/search/tv?api_key=44637956b9084a5c4eb306d80e3f63ea&query=" + this.userResearch
			axios
			.get(apiObj)
			.then((obj) => {
				this.seriesArr = obj.data.results;
				// // used to send series Array info to parent(App)
				this.$emit('correlatedSeries', this.seriesArr)
				console.log(this.seriesArr)
			})
		},
		// use both function on click
		checkSeriesFilms() {
			this.saveUserSearchFilms();
			this.saveUserSearchSeries();				
		}

	}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
	header {
		padding: .5em 2em ;
		display: flex;
		justify-content: space-between;
		align-items: center;
		color: var(--clr-txt-primary-500);
		background-color: var(--clr-neutral-900);
	}
	#input-search, button {
		font-size: .8rem;
		padding: 0.2em 0.5em;
		border: 0;
	}
	button {
		background-color: var(--clr-txt-primary-500);
	}
</style>