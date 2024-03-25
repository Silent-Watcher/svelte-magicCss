<script lang="ts">
	import { Label, Select } from 'flowbite-svelte';
	import ColorPicker, { ChromeVariant } from 'svelte-awesome-color-picker';
	import Code from '../../components/Code.svelte';
	import Rslider from '../../components/UI/Rslider.svelte';
	let angle = { min: 0, max: 360, values: [0] };
	let [hex1, hex2, selected]: string[] = ['rgb(65, 105, 225)', 'rgb(2, 0, 36)', 'linear'];
	let gradientTypes = [
		{ value: 'linear', name: 'linear' },
		{ value: 'radial', name: 'radial' }
	];
	$: gradientValue = `background: ${selected}-gradient(${selected === 'radial' ? 'circle,' : angle.values[0] + 'deg,'} ${hex1},${hex2})`;
</script>

<main class="container mx-auto mt-10">
	<section style={gradientValue} class="screen mx-auto h-72 w-2/3 rounded-xl"></section>
	<section class="mx-auto mt-10 grid grid-cols-1 items-center justify-center lg:grid-cols-3">
		<div class="text-center">
			<ColorPicker
				bind:hex={hex1}
				--cp-border-color="none"
				--cp-bg-color="none"
				--cp-input-color="#ddd"
				--focus-color="#2563eb"
				components={ChromeVariant}
				sliderDirection="horizontal"
				isDialog={false}
			/>
		</div>
		<div class="items-center justify-center text-center">
			<Label class="mb-9">
				Gradient Type
				<Select class="mt-2" items={gradientTypes} bind:value={selected} />
			</Label>
			{#if selected === 'linear'}
				<!-- content here -->
				<Rslider
					bind:min={angle.min}
					bind:max={angle.max}
					bind:values={angle.values}
					label="Angle"
				/>
			{/if}
			<Code code={gradientValue} />
		</div>
		<div class="mt-10 text-center lg:mt-0">
			<ColorPicker
				bind:hex={hex2}
				--cp-border-color="none"
				--cp-bg-color="none"
				--cp-input-color="#ddd"
				--focus-color="#2563eb"
				components={ChromeVariant}
				sliderDirection="horizontal"
				isDialog={false}
			/>
		</div>
	</section>
</main>
