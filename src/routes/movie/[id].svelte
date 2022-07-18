<script context="module">
    export async function load({fetch, params}) {
        const id = params.id;
        const apiKey = '65f92f0b969c943799b54b78ce0f5773';
        const url = `https://api.themoviedb.org/3/movie/${id}?api_key=${apiKey}&language=en-US`;
        const res = await fetch(url);
        const movieDetail = await res.json();
        if (res.ok) {
            return {
                props: { movieDetail }
            };
        }
        
    }
</script>

<script>
    import { fly } from 'svelte/transition';
    export let movieDetail;
</script>

<style>
    h1 {
        padding: 1rem 0rem 2rem;
    }
    p {
        padding: 1rem 0rem;
    }
    .img-container {
        width: 100%;
    }
    img {
        width: 100%;
        border-radius: 1rem;
    }
    .movie-details {
        margin: 2rem 20%;
    }
    span {
        font-weight: bold;
    }
    .genres {
        font-weight: normal;
    }
</style>

<div class="movie-details" in:fly={{ y: 50, duration: 500, delay: 500 }} out:fly={{ duration: 500 }}>
    <div class="img-container">
        <img 
            src={"https://image.tmdb.org/t/p/original" + movieDetail.backdrop_path} 
            alt="{movieDetail.title}"
        />
    </div>
    <div class="text-container">
        <h1>{movieDetail.title}</h1>
        <p class="overview">{movieDetail.overview}</p>
        <p>
            <span>Release Date:</span>
            {movieDetail.release_date} <br/>
        </p>
        <p>
            <span>Original title:</span>
            {movieDetail.original_title} <br/>
        </p>
        <p>
            <span>Genres:</span>
            {#each movieDetail.genres as genre} 
                {#if movieDetail.genres[movieDetail.genres.length - 1].name != genre.name}
                    <span class="genres">{genre.name}, &nbsp</span>
                {:else}
                    <span class="genres">{genre.name}</span>
                {/if}
            {/each}
            <br/>
        </p>
        <p>
            <span>Original language:</span>
            {movieDetail.original_language} <br/>
        </p>
        <p>
            <span>Runtime:</span>
            {movieDetail.runtime} min <br/>
        </p>
        <p>
            <span>Raiting:</span>
            {movieDetail.vote_average} <br/>
        </p>
    </div>
</div>