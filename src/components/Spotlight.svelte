<script>
	let el;

	let right = '50%';
	let top = '50%';
	let max = 80;
	let min = 1;

	setInterval(() => {
		right = `${Math.floor(Math.random() * (max - min + 1) + min)}%`;
		top = `${Math.floor(Math.random() * (max - min + 1) + min)}%`;
	}, 1000);
</script>

<div
	style:right
	style:top
	bind:this={el}
	class="absolute w-1/4 h-0 transition-all ease-in duration-1000  bg-transparent move"
>
	<!-- <div class="spotlight w-full h-full" /> -->
	<div class="flex items-stretch spotlight">
		<div class="spotlight w-full" />
		<img class="bg-transparent" src="./logo_midgreen_spotlight.png" alt="spotlight" />
	</div>
</div>

<style>
	.spotlight {
		border-radius: 10000px;
		-webkit-box-shadow: 68px 93px 133px -18px rgba(0, 0, 0, 0.75);
		-moz-box-shadow: 68px 93px 133px -18px rgba(0, 0, 0, 0.75);
		box-shadow: 68px 93px 133px -18px rgba(0, 0, 0, 0.75);
	}
	.move {
	}
</style>
