<script>
  import { onMount } from 'svelte';

  let books = []; /* sparar böcker från db */

  /* körs när komponenten visas första gången */
  onMount(async () => {
    const response = await fetch('http://localhost:3001/books'); /* data från db */
    books = await response.json(); /* svaret blir till js objekt */
  });
</script>

<h2>Här kommer biblioteket</h2>

<!-- loopar igenom alla böcker i arrayen -->
{#each books as book}
  <div>
    <img src={book.image} alt={book.title} width="150" />
    <h3>{book.title}</h3>
    <p>{book.author}</p>
    <p>{book.year}</p>
  </div>
{/each}