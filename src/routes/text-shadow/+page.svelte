<script>
	import ColorPicker, { ChromeVariant } from 'svelte-awesome-color-picker';
	import Code from '../../components/Code.svelte';
	import Rslider from '../../components/UI/Rslider.svelte';
	let hex = '#2563eb';
	let x = { min: -40, max: 40, values: [20] };
	let y = { min: -40, max: 40, values: [10] };
	let blur = { min: 0, max: 20, values: [10] };
	$: textShadowValue = `text-shadow: ${x.values[0]}px ${y.values}px ${blur.values[0]}px ${hex}`;
</script>

<main class="container mt-10 grid grid-cols-1 gap-2 text-center lg:mt-0 lg:grid-cols-3">
	<section>
		<Rslider bind:min={x.min} bind:max={x.max} bind:values={x.values} label="X" />
		<Rslider bind:min={y.min} bind:max={y.max} bind:values={y.values} label="Y" />
		<Rslider bind:min={blur.min} bind:max={blur.max} bind:values={blur.values} label="Blur" />
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
		<div class="mb-20 flex h-80 w-80 items-center justify-center rounded-lg bg-gray-300">
			<p style={textShadowValue} class="text-2xl">John Doe</p>
		</div>
		<Code code={textShadowValue} />
	</section>
</main>
