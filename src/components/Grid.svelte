<script lang="ts">
	import { text } from '@sveltejs/kit';
	import { createEventDispatcher } from 'svelte';
	let dispatch = createEventDispatcher();
	import { writable } from 'svelte/store';

	export let rows: number;
	export let columns: number;

	export let height = 100;
	export let width = 100;

	export let displayNum = false;

	let selectedBtns = Array(rows * columns).fill(false);
	let selectedBtnsStore = writable(selectedBtns);

	const splash = (i: number, j: number) => (i - 1) * columns + j - 1;

	const handleClick = (i: number, j: number) => {
		const index = splash(i, j);
		selectedBtns[index] = !selectedBtns[index];
		selectedBtnsStore.set(selectedBtns);
	};
</script>

{#each Array(rows) as a, i}
	<div class="flex">
		{#each Array(columns) as b, j}
			{#if selectedBtns[splash(i, j)]}
				<button
					class="outline-1 outline-double outline-gray-950 bg-green-400 hover:bg-red-400"
					style={`height: ${height}px; width: ${width}px;`}
					on:click={() => handleClick(i, j)}>{displayNum ? 1 : ''}</button
				>{:else}
				<button
					class="outline-1 outline-double outline-gray-950 hover:bg-green-300 bg-white"
					style={`height: ${height}px; width: ${width}px;`}
					on:click={() => handleClick(i, j)}>{displayNum ? 0 : ''}</button
				>{/if}
		{/each}
	</div>
{/each}
