<script>
    import GameBoard from '../components/GameBoard.svelte'
</script>

<main>

    <div class="kid-friendly">
        <h1>Find the Barking Animal</h1>
    </div>
    <GameBoard />

    <footer>
      <p>&copy; 2023 MidJourney. All rights reserved.</p>
      <p>All images created by MidJourney.</p>
    </footer>
</main>

<style>
:global(body) {
  /* This sets the background color to a calming blue gradient */
  background: linear-gradient(to right, #add8e6, #90ee90); 
}

 @keyframes sparkle {
    0% {
      opacity: 1;
      color: white;
    }
    5% {
      opacity: 0.5;
      color: yellow;
    }
    30% {
      opacity: 1;
      color: purple;
    }
    95% {
      opacity: 0.5;
      color: yellow;
    }
    100% {
      opacity: 1;
      color: white;
    }
  }

.kid-friendly {
  font-family: 'Patrick Hand', cursive;
  animation: sparkle 1s ease-in-out infinite;
}

footer {
  padding: 10px;
  text-align: center;
  font-size: 14px;
  color: #888;
  background: linear-gradient(to right, #add8e6, #90ee90); 
}

</style>