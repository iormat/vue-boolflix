<template>
	<header>
		<h1> BoolFlix </h1>
		<div>
			<label for="input-search">
				<input id="input-search" type="text">
			</label>
			<button> Search </button>
		</div>
	</header>
</template>

<script>
export default {
  name: 'AppHeader',
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
