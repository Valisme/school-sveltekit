<script lang="ts">
	import { onMount } from 'svelte';
    import {blur} from 'svelte/transition'
	const welcome: string = "Welcome to School's Website";
	let typedWelcome: string = '';
	let index: number = 0;
    let typed:boolean = false;
	onMount( () => {
		const typing = setInterval(async() => {
			if (index < welcome.length) {
				typedWelcome += welcome[index];
				index++;
			} else {
                clearInterval(typing)
                typed = true;
				return;
			}
		},50);
	});
</script>

<div class="flex flex-col">
    <div class="h-96 flex flex-col items-center gap-4 justify-center ">
        <p class="text-7xl font-semibold text-white text-center">{typedWelcome}</p>
        {#if typed}
        <p class="text-3xl font-medium text-white text-center mt-6transition-all duration-0 ease-linear" transition:blur="{{amount:10}}">Education is key for <span class="text-yellow-400">Bright</span> Future</p>
        {/if}
    </div>
</div>
