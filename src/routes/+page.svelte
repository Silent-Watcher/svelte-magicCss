<script lang="ts">
	import ColorPicker, { ChromeVariant } from 'svelte-awesome-color-picker';
	import Rslider from './../components/UI/Rslider.svelte';
	let x = { min: -130, max: 130, values: [0] };
	let y = { min: -130, max: 130, values: [0] };
	let blur = { min: 0, max: 130, values: [65] };

	let hex = '#2563eb';
</script>

<main class="container mt-16 grid grid-cols-1 gap-2 text-center lg:grid-cols-3">
	<section>
		<Rslider bind:min={x.min} bind:max={x.max} bind:values={x.values} label="X" />
		<Rslider bind:min={y.min} bind:max={y.max} bind:values={y.values} label="Y" />
		<Rslider bind:min={blur.min} bind:max={blur.max} bind:values={blur.values} label="blur" />
	</section>
	<section class="mx-auto flex content-center items-center text-center">
		<ColorPicker
			bind:hex
			--cp-border-color="none"
			--cp-bg-color="none"
			--cp-input-color="#ddd"
			--focus-color="#2563eb"
			components={ChromeVariant}
			sliderDirection="horizontal"
			isDialog={false}
		/>
	</section>
	<section class="flex flex-col content-between items-center">
		<div style="background-color: {hex};" class="mb-auto h-52 w-52 rounded-lg bg-gray-500"></div>
		<p class="dark:text-white">result ...</p>
	</section>
</main>
