<script lang="ts">
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();
	const handleClick = (i: any) => {
		dispatch('changeSlide', i);
	};
</script>

<div class="absolute m-3 -bottom-0 -right-0">
	<button
		class="rounded-full bg-white shadow-2xl w-10 h-10 hover:bg-inherit hover:text-white hover:border-white hover:border-4"
		on:click={() => handleClick(-1)}><i class="fa-solid fa-arrow-left" /></button
	>

	<button
		class="rounded-full bg-white shadow-2xl w-10 h-10 hover:bg-inherit hover:text-white hover:border-white hover:border-4"
		on:click={() => handleClick(1)}><i class="fa-solid fa-arrow-right" /></button
	>
</div>
