<script>
	import { darkMode } from '../store/darkMode';
	let title = 'Ninja Gaming Guides';

	const updateTitle = () => {
		title = 'something completely different';
	};

	let darkModeValue;
	const handleClick = () => {
		darkMode.update((value) => {
			console.log(value);
			return !value;
		});
	};
	darkMode.subscribe((value) => {
		darkModeValue = value;
	});
</script>

<div class="index">
	<h2>{title}</h2>
	<p>
		Lorem ipsum dolor, sit amet consectetur adipisicing elit. Maxime sunt laboriosam vitae labore
		veniam eveniet esse sequi ea. Explicabo consequuntur provident iure, asperiores distinctio
		nostrum pariatur eligendi excepturi tenetur eaque?
	</p>
	<a href="/guides">View Guides</a>
	<a href="/about">About</a>
	<button on:click={handleClick}>Update Dark Mode</button>
	<p>{$darkMode}</p>
	<p>{darkModeValue}</p>
</div>

<style>
	.index {
		text-align: center;
		display: block;
		margin: 20px auto;
	}
</style>
