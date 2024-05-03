<svelte:head>
	<title>Typography</title>
	<meta name="description" content="Typography this app" />
</svelte:head>

<script>
	import { bookData } from '../bookData';		
	import Search from '../Search.svelte';

	// For Search Input
	let searchTerm = "";
	// resets language menu if search input is used
	$: if (searchTerm) selectedLang = ""; 
	
	const searchBooks = () => {	
		return filteredBooks = bookData.filter(book => {
			let bookTitle = book.title.toLowerCase();
			return bookTitle.includes(searchTerm.toLowerCase())
		});
	}
</script>

<div class="text-column">
	<h1>Typography this app</h1>

	<Search bind:searchTerm on:input={searchBooks} />
	<p>
		This is a <a href="https://kit.svelte.dev">SvelteKit</a> app. You can make your own by typing the
		following into your command line and following the prompts:
	</p>

	<pre>npm create svelte@latest</pre>

	<p>
		The page you're looking at is purely static HTML, with no client-side interactivity needed.
		Because of that, we don't need to load any JavaScript. Try viewing the page's source, or opening
		the devtools network panel and reloading.
	</p>

	<p>
		The <a href="/sverdle">Sverdle</a> page illustrates SvelteKit's data loading and form handling. Try
		using it with JavaScript disabled!
	</p>
</div>
