<script>
  import { onMount } from 'svelte';
  import Book from './Book.svelte';

  let books = []; /* sparar böcker från db */

  /* körs när komponenten visas första gången */
  onMount(async () => {
    const response = await fetch('http://localhost:3001/books'); /* data från db */
    books = await response.json(); /* svaret blir till js objekt */
  });
</script>

<h2>Böcker vi har:</h2>

<!-- loopar igenom alla böcker i arrayen -->
<div class="library">
    {#each books as book}
        <Book book={book} />
    {/each}
</div>

<style>
    .library {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: 1rem;
    }

    h2 {
        margin-bottom: 30px;
    }
</style>