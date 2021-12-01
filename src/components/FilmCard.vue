<template>
    <li class="film-card">
        <a href="">
            <img src="" alt="">

        </a>
    </li>
</template>

<script>
export default {
  name: 'FilmCard',
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
	.film-card {
        width: calc(100% / 6);
        min-width: 20ch;
	}
</style>