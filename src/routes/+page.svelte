<script lang="ts">
	import { onMount } from 'svelte';
	import { blur, fly } from 'svelte/transition';
	const welcome = "Welcome to School's Website";
	let typedWelcome = '';
	let y = 0;
	let index = 0;
	let indexTwo = 0;
	let typed = false;
	let typedTwo = false;
	let num1: HTMLElement | undefined;

	onMount(() => {
		const typing = setInterval(() => {
			if (index < welcome.length) {
				typedWelcome += welcome[index];
				index += 1;
			} else {
				clearInterval(typing);
				typed = true;
				return;
			}
		}, 50);
	});
	function onScroll() {
		// Get first section progress
		// Will return 0 if section out of view
		const bottom = num1?.getBoundingClientRect().bottom ?? 0;
		// Check if the bottom is less than zero
		if (bottom < 0) {
			typedTwo = true;
		}
	}
</script>

<svelte:window on:scroll={() => onScroll()} bind:scrollY={y} />
<svelte:body class={typed ? '' : 'overflow-y-hidden'} />
<div class="flex flex-col gap-40">
	<div class="h-screen flex flex-col items-center gap-4 justify-center mt-16" bind:this={num1}>
		<p class="text-7xl font-semibold text-white text-center">{typedWelcome}</p>
		{#if typed}
			<p
				class="text-3xl font-medium text-white text-center mt-6 transition-all duration-0 ease-linear"
				transition:blur={{ amount: 10 }}
			>
				Education is key for <span class="text-yellow-400">Bright</span> Future
			</p>
		{/if}
	</div>
	<div class="h-screen bg-cyan-500 p-10 pt-20 snap-center flex flex-row gap-20">
		<img src="/sekolah.jpeg" alt="foto sekolah" class="w-96 h-[32rem]" />
		{#if typedTwo}<p
				class="text-8xl font-semibold text-white text-start"
				transition:blur={{ amount: 5 }}
			>
				We Educate, Aiming For the Best
			</p>{/if}
	</div>
</div>
