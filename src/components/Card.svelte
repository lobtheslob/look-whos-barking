<script lang="ts">

    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    export let animal: { name: string; image: string; isBarking: boolean };
    let flipped = false;
    let isBarking = false;


    function flipCard() {
        flipped = !flipped;
        if (flipped && animal.isBarking) {
            dispatch('bark');
        }
    }
</script>

<!-- the rest of the component remains the same -->
<div class="card" class:is-flipped={flipped} on:click={flipCard}>
    {#if flipped}
    <div class="card-face front">
        <img src={`/images/${animal.image}`} alt={animal.name}>
    </div>
    {:else if !flipped}
    <div class="card-face back">
        <img src={`/images/back-card.jpg`} alt={animal.name}>
    </div>
    {/if}
</div>

<style>
    .card {
        perspective: 1000px;
        /* This sets the font for the index cards to Bubblegum Sans */
        font-family: 'Bubblegum Sans', cursive; 
        /* Add a border to make the card stand out */
        border: 2px solid black; 
        /* Add some padding inside the card */
        padding: 10px; 
    }

    .card-face {
        width: 100%;
        height: 100%;
        transition: transform 0.6s;
    }

    .is-flipped {
        transform: rotateY(180deg);
    }

    .card-face.front {
        transform: rotateY(180deg);
    }

    .card-face.back{
        transform: rotateY(180deg);
    }

    .card-face img {
        width: 100%;
        height: 100%;
        object-fit: cover; /* this will ensure the image covers the entire area of the card without distorting the aspect ratio */
    }

</style>