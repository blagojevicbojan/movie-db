<script>
    import {goto} from '$app/navigation';

    let inputValue = '';

    function search() {
        goto('/search/' + inputValue);
    }
</script>

<style>
    .search {
        display: flex;
        justify-content: left;
        align-items: center;
    }
    input {
        margin: 1rem;
        width: 100%;
        border: 2px solid rgb(150, 150, 150);
        font-size: 1rem;
        padding: 0.5rem 0.1rem;
        font-weight: bold;
        border-radius: 10px;
        padding: 1rem;
    }

    button {
        font-size: 1rem;
        padding: 0.5rem 0.1rem;
        color: white;
        font-weight: bold;
        border: none;
        cursor: pointer;
        border-radius: 10px;
        background: rgba(96, 110, 201);
        height: 100%;
        padding: 1rem;
    }

    @media screen and (min-width: 600px) {
        input {
            width: 50%;
        }
    }

    @media screen and (min-width: 992px) {
        input {
            width: 40%;
        }
    }
</style>


<form on:submit|preventDefault={search} class="search">
    <input 
        placeholder="Search movie"
        bind:value={inputValue} 
        name="search_movie" 
        type="text" 
    >
    {#if inputValue}
        <button>Search</button>
    {/if}       
</form>
    