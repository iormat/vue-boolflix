<template>
	<div id="app">
		<AppHeader/>
		<AppMain/>
	</div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'

export default {
	name: 'App',
		components: {
			AppHeader,
			AppMain,
		}
	}
</script>

<style lang="scss">
	:root {
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
</style>
