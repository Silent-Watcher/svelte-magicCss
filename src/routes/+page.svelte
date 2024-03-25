<script lang="ts">
	import ColorPicker, { ChromeVariant } from 'svelte-awesome-color-picker';
	import Code from '../components/Code.svelte';
	import Rslider from './../components/UI/Rslider.svelte';
	let x = { min: -130, max: 130, values: [0] };
	let y = { min: -130, max: 130, values: [0] };
	let blur = { min: 0, max: 130, values: [65] };
	let spread = { min: -50, max: 50, values: [0] };

	let hex = '#2563eb';
	$: boxShadowValue = `box-shadow: ${hex} ${x.values[0]}px ${y.values}px ${blur.values[0]}px ${spread.values[0]}px;`;
</script>

<main class="container grid grid-cols-1 gap-2 text-center lg:grid-cols-3">
	<section>
		<Rslider bind:min={x.min} bind:max={x.max} bind:values={x.values} label="X" />
		<Rslider bind:min={y.min} bind:max={y.max} bind:values={y.values} label="Y" />
		<Rslider bind:min={blur.min} bind:max={blur.max} bind:values={blur.values} label="Blur" />
		<Rslider
			bind:min={spread.min}
			bind:max={spread.max}
			bind:values={spread.values}
			label="Spread"
		/>
	</section>
	<section class="mx-auto mb-12 flex items-center justify-center text-center lg:mb-0">
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
	<section class="flex flex-col items-center justify-center">
		<div style="{boxShadowValue};" class="mb-20 h-52 w-52 rounded-lg bg-gray-500"></div>
		<Code code={boxShadowValue} />
	</section>
</main>
