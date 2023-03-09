<script lang="ts">
	import { onDestroy } from 'svelte';

	let el: HTMLDivElement;

	let left = '80%';
	let top = '10%';
	let leftMax = 70;
	let topMax = 80;
	let min = 1;

	let box = '0px -300px 133px 0px rgba(0, 0, 0, 0.75)';

	const spotlightPositionInterval = setInterval(() => {
		const rightPos = getRandomNumber(min, leftMax);
		const topPos = getRandomNumber(min, topMax);
		left = `${rightPos}%`;
		top = `${topPos}%`;
	}, 1000);

	const elPosInterval = setInterval(() => {
		if (el) {
			triggerShadowChange(el.getBoundingClientRect());
		}
	}, 10);

	const triggerShadowChange = (bound: { left: number; top: number; width: number }) => {
		const { left, top, width } = bound;
		const percentLeft = Math.round(Math.floor(((left + width / 2) / window.innerWidth) * 100));
		const percentTop = Math.round(Math.floor((top / window.innerHeight) * 100));
		let boxX = percentLeft === 50 ? 0 : 700 * ((percentLeft - 50) / 100) * -1;
		let boxY = percentTop === 50 ? 0 : 1000 * ((percentTop - 50) / 100) * -1;

		box = `${boxX}px ${boxY}px 133px 0px rgba(0, 0, 0, 0.75)`;
	};

	const getRandomNumber = (min: number, max: number): number => {
		return Math.floor(Math.random() * (max - min + 1) + min);
	};

	onDestroy(() => {
		clearInterval(spotlightPositionInterval);
		clearInterval(elPosInterval);
	});

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
