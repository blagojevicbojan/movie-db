<script context="module">
    export async function load({fetch}) {
        //const apiKey = '65f92f0b969c943799b54b78ce0f5773';
        const url = `https://api.themoviedb.org/3/movie/popular?api_key=${import.meta.env.VITE_API}&language=en-US&page=1`;
        const res = await fetch(url);
        const data = await res.json();
        if (res.ok) {
            return {
                props: {popular: data.results}
            }
        }     
    }
</script>

<script>
    import PopularMovies from "../components/PopularMovies.svelte"; 
    import SearchMovies from "../components/SearchMovies.svelte";
    import { fly } from 'svelte/transition';
    
    export let popular;
</script>

<section in:fly={{ y: 50, duration: 500, delay: 500 }} out:fly={{ duration: 500 }}>
    <SearchMovies />
    <PopularMovies {popular} />
</section>

