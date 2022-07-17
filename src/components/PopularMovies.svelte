<script>
    import MovieCard from "./MovieCard.svelte";

    export let popular;
</script>

<style>
    h3 {
        padding: 0 1rem;
    }

    .popular-movies {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        row-gap: 2rem;
        column-gap: 1rem;
    }
</style>

<h3>Popular Movies</h3>

<div class="popular-movies">
    {#each popular as movie}
        <MovieCard {movie} />
    {/each}
</div>