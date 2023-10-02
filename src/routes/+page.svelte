<script lang="ts">
	// Import necessary modules and define ArticleData interface

	import Article from '../components/Article.svelte';
	import { onMount, afterUpdate } from 'svelte';

	interface ArticleData {
		title: string;
		image: string;
		image_alt: string;
		content: string;
		link: string;
		credit: string;
	}

	let articles: ArticleData[] = [];
	const maxArticles = 100;
	
	const generateRandomArticle = (): ArticleData => {
		// Generate random article data here
		return {
			title: 'Random Title',
			image: 'https://www.quiktrip.com/app/uploads/2021/10/MicrosoftTeams-image-5.jpg',
			image_alt: 'Image Alt Text',
			content: 'Here is some random content about hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdog hotdoghotdog hotdoghotdog hotdoghotdog hotdoghotdog hotdog',
			link: 'https://www.google.com/search?q=eggs',
			credit: 'Hotdog fan #1'
		};
	};
	
	// Function to load more random articles
	const loadMoreRandomArticles = () => {
		const numNewArticles = 16; // Number of new articles to generate and append
		for (let i = 0; i < numNewArticles; i++) {
			//Let compiler know an update was done as svelte just hooks assignments and not mutations
			articles.push(generateRandomArticle());
		}
		articles = [...articles]; // Trigger update
		console.log(articles);
	};

	onMount(() => {
		// Load initial set of articles
		loadMoreRandomArticles();

		// Add an event listener to the window to detect scrolling
		window.addEventListener('scroll', () => {
			// Calculate how close to the bottom the user is
			const scrollY = window.scrollY;
			const windowHeight = window.innerHeight;
			const documentHeight = document.body.offsetHeight;
			if (scrollY + windowHeight >= documentHeight - 200) {
				loadMoreRandomArticles(); // Load more articles when close to the bottom
			}
		});
	});
</script>

<div class="flex flex-wrap justify-center">
	{#each articles as article}
		<div class="w-full sm:w-1/2 md:w-1/3 lg:w-1/4 p-2">
			<Article {...article} />
		</div>
	{/each}
</div>

<style>
	/* Add your styles here if needed */
</style>
