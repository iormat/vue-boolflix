<template>
    <main>
        <ul id="cards-container">
            <FilmCard/>
        </ul>
    </main>
</template>

<script>
import FilmCard from "./FilmCard.vue";
import axios from "axios";

export default {
  name: 'AppMain',
  components: {
      FilmCard,
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
	main {
		background-color: var(--clr-neutral-500);
        height: calc(100vh - 75px);
	}
    #card-container {
        width: 70%;
        margin: 0 auto;
        display: flex;
        flex-flow: row wrap;
        justify-content: flex-start;
    }
</style>
