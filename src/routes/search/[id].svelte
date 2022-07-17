<script context="module">
    export async function load({fetch, params}) {
        const id = params.id;
        const apiKey = '65f92f0b969c943799b54b78ce0f5773';
        const url = `https://api.themoviedb.org/3/search/movie?api_key=${apiKey}&language=en-US&query=${id}&page=1&include_adult=false`;
        const res = await fetch(url);
        const data = await res.json();
        if (res.ok) {
            return {
                props: { searchedMovie: data.results }
            }
        }
    }
</script>

<script>
    import MovieCard from "../../components/MovieCard.svelte";

    export let searchedMovie;
</script>

<style>
    .searched-movies {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        column-gap: 1rem;
        row-gap: 2rem;
        height: 20vh;
    }
</style>

<div class="searched-movies">
    {#each searchedMovie as movie}
        <MovieCard {movie} />
    {/each}
</div>