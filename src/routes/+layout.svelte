<script lang="ts">
	import '../app.css';
</script>

<nav class="bg-lime-600 w-full h-14 flex flex-row items-center p-6 font text-xl text-white fixed">
	<ul class="flex flex-row gap-4">
		<li><a href="/">Home</a></li>
		<li><a href="/class">Class</a></li>
		<li><a href="/forum">Forum</a></li>
	</ul>
	<ul class="ml-auto flex flex-row gap-4">
		<li>Sign In</li>
		<li>Login</li>
	</ul>
</nav>
<slot />

<style lang="postcss">
	:global(html) {
		background-color: theme(colors.teal.950);
		scroll-behavior: smooth;
	}
</style>
