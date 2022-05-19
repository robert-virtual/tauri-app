<script>
    let quotePromise = fetch("https://programming-quotes-api.herokuapp.com/quotes/random").then(x=>x.json())
</script>

<h1>About</h1>
{#await quotePromise}
<p>loading...</p>
{:then quote}
<div>
<p>{quote.en}</p>
<p>{quote.author}</p>
</div>
{/await}