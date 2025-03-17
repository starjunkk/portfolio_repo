<script>
	import Post from "./Post.svelte";
	
	let { data } = $props();
</script>

{JSON.stringify(data)}

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<div class="container">
	<h1>Portfolio</h1>

	<div class="posts">
		{#each data.works as work} 
			<Post work={work}></Post>
		{/each}
	</div>
</div>

<style>
	body {
		background-color: #f5f5f5;
		font-family: Arial, sans-serif;
		color: #333;
		margin: 0;
		padding: 0;
	}

	.container {
		max-width: 800px;
		margin: 40px auto;
		padding: 20px;
		text-align: center;
	}

	h1 {
		font-size: 2rem;
		margin-bottom: 20px;
	}

	.posts {
		display: flex;
		flex-direction: column;
		gap: 40px;
	}
</style>
