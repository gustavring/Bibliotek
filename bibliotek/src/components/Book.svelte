<script>
    export let book;
</script>

<div class="book-wrapper">
    <img src={book.image} alt={book.title} width="150" />
    <h3>{book.title}</h3>
    <p>{book.author}</p>
    <p>{book.year}</p>
</div>