<script lang="ts">
	import Grid from './../components/Grid.svelte';
	import SlideChangeButtons from './../components/SlideChangeButtons.svelte';
	import Footer from '../components/Footer.svelte';

	let currentSlide = 1;
	const handleChangeSlide = (e: any) => {
		let changeFactor = e.detail;
		if (changeFactor == -1) {
			if (currentSlide != 1) {
				currentSlide = currentSlide - 1;
			}
		} else {
			if (currentSlide != 2) {
				currentSlide = currentSlide + 1;
			}
		}
	};
</script>

<div class="h-screen w-screen flex flex-col justify-center items-center bg-gray-800 relative">
	<div class="absolute rounded-full h-full w-full bg-purple-500 blur-2xl animation-resize" />
	<div class="w-2/3 h-2/3 rounded-2xl shadow-2xl bg-gray-900 flex z-10 relative animation-appear">
		<div class="h-min w-min absolute top-10 left-10">
			{#if currentSlide == 1}
				<Grid rows={10} columns={10} height={40} width={40} />
			{:else if currentSlide == 2}<span class="text-6xl text-white">HIIII</span>{/if}
		</div>
		<SlideChangeButtons on:changeSlide={handleChangeSlide} />
	</div>
</div>
