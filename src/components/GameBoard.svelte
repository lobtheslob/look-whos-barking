<script lang="ts">
    import Card from './Card.svelte';
 //   import { CustomEvent } from 'svelte';
    
    let audioElement: HTMLAudioElement;
    interface Animal {
        name: string;
        image: string;
        isBarking: boolean;
    }

    let animals: Animal[] = [
        { name: 'Dog', image: 'dog.jpg', isBarking: true },
        { name: 'Cat', image: 'cat.jpg', isBarking: false },
        { name: 'Seal', image: 'seal.jpg', isBarking: true },
        { name: 'Bird', image: 'bird.jpg', isBarking: false},
    ];

    // randomize the array
    animals = animals.sort(() => Math.random() - 0.5);

    function handleBark(event: CustomEvent) {

        audioElement.src = "sounds/bark.wav"; // Update the path to the WAV file
        audioElement.play();
        alert('You found a barking animal!');
    }
</script>

<div class="game-board">
    {#each animals as animal}
        <audio bind:this={audioElement}></audio>
        <Card {animal} on:bark={handleBark} />
    {/each}
</div>

<style>
    .game-board {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 10px;
    }
</style>