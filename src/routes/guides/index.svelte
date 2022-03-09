<script context="module">
	export const load = async ({ fetch }) => {
		const response = await fetch('https://jsonplaceholder.typicode.com/posts');
		const guides = await response.json();

		if (response.ok) {
			return {
				props: {
					guides
				}
			};
		}

		return {
			status: response.status,
			error: new Error('Could not fetch the guides')
		};
	};
</script>

<script>
	export let guides;
</script>

<div class="guides">
	<ul>
		{#each guides as guide}
			<a sveltekit:prefetch href="/guides/{guide.id}">{guide.title}</a>
		{/each}
		<li>
			<a href="/">guide 1</a>
			<a href="/">guide 2</a>
		</li>
	</ul>
</div>

<style>
	.guides {
		margin-top: 20px;
	}
	ul {
		list-style-type: none;
		padding: 0;
	}
	a {
		display: inline-block;
		margin-top: 10px;
		padding: 10px;
		border: 1px dotted rgba(255, 255, 255, 0.2);
	}
</style>
