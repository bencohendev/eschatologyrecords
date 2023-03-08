<script lang="ts">
	import { onDestroy } from 'svelte';

	let el: HTMLDivElement;

	let left = '0%';
	let top = '60%';
	let leftMax = 100;
	let topMax = 100;
	let min = 1;

	let box = '350px -200px 133px 0px rgba(0, 0, 0, 0.75)';

	// const spotlightPositionInterval = setInterval(() => {
	// 	const rightPos = getRandomNumber(min, leftMax);
	// 	const topPos = getRandomNumber(min, topMax);
	// 	left = `${rightPos}%`;
	// 	top = `${topPos}%`;
	// }, 5000);

	// const elPosInterval = setInterval(() => {
	// 	if (el) {
	// 		triggerShadowChange(el.getBoundingClientRect());
	// 	}
	// }, 100);

	const triggerShadowChange = (bound: any) => {
		const { x, y, bottom, left, right, top, height, width } = bound;
		const percentLeft = Math.round(Math.floor(((left + width / 2) / window.innerWidth) * 100));
		const percentTop = Math.round(Math.floor((top + height / 2 / window.innerHeight) * 100));
		console.log(
			'🚀 ~ file: Spotlight.svelte:32 ~ triggerShadowChange ~ scrollPercent:',
			percentLeft
		);
	};

	const getRandomNumber = (min: number, max: number): number => {
		return Math.floor(Math.random() * (max - min + 1) + min);
	};

	// onDestroy(() => {
	// 	clearInterval(spotlightPositionInterval);
	// 	clearInterval(elPosInterval);
	// });

	$: {
		if (el) {
			triggerShadowChange(el.getBoundingClientRect());
		}
	}
</script>

<div
	style:left
	style:top
	bind:this={el}
	class="absolute w-1/4 h-0 ease-in duration-1000 bg-transparent transition-all"
>
	<div class="flex items-stretch rounded-full" style:box-shadow={box}>
		<img class="bg-transparent" src="./logo_midgreen_spotlight.png" alt="" />
	</div>
</div>

<style>
</style>
