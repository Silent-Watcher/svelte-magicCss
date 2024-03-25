<script lang="ts">
	import { Label, Radio, Select } from 'flowbite-svelte';
	import Code from '../../components/Code.svelte';
	import Rslider from '../../components/UI/Rslider.svelte';
	let unit: string = 'px';
	let selected: string = 'ss';
	let BorderRadiusTypes = [
		{ value: 'ss', name: 'same on all sides' },
		{ value: 'ds', name: 'different on all sides' }
	];
	let px = { min: 0, max: 100, values: [50] };
	let pxTL = { min: 0, max: 100, values: [50] };
	let pxTR = { min: 0, max: 100, values: [50] };
	let pxBL = { min: 0, max: 100, values: [50] };
	let pxBR = { min: 0, max: 100, values: [50] };
	let percentTL = { min: 0, max: 50, values: [25] };
	let percentTR = { min: 0, max: 50, values: [25] };
	let percentBL = { min: 0, max: 50, values: [25] };
	let percentBR = { min: 0, max: 50, values: [25] };
	let percent = { min: 0, max: 50, values: [25] };

	$: borderRadiusValue = '';
	$: if (selected == 'ss') {
		if (unit == 'px') {
			borderRadiusValue = `border-radius: ${px.values[0]}px;`;
		} else {
			borderRadiusValue = `border-radius: ${percent.values[0]}%;`;
		}
	} else {
		if (unit == 'px') {
			borderRadiusValue = `border-radius: ${pxTL.values[0]}px ${pxTR.values[0]}px ${pxBR.values[0]}px ${pxBL.values[0]}px `;
		} else {
			borderRadiusValue = `border-radius: ${percentTL.values[0]}% ${percentTR.values[0]}% ${percentBR.values[0]}% ${percentBL.values[0]}%;`;
		}
	}
</script>

<main class="container mt-14 grid grid-cols-1 text-center lg:grid-cols-2">
	<section>
		<Label class="mb-9">
			Which side
			<Select class="mt-2" items={BorderRadiusTypes} bind:value={selected} />
		</Label>
		<p class="dark:text-white">Unit</p>
		<div class="mb-4 flex flex-col items-center justify-center gap-2 py-4">
			<Radio bind:group={unit} color="blue" value="px">px</Radio>
			<Radio bind:group={unit} color="blue" value="%">%</Radio>
		</div>
		{#if selected == 'ss'}
			{#if unit == 'px'}
				<Rslider bind:min={px.min} bind:max={px.max} bind:values={px.values} label="Angle" />
			{:else}
				<Rslider
					bind:min={percent.min}
					bind:max={percent.max}
					bind:values={percent.values}
					label="Angle"
				/>
			{/if}
		{:else}
			<div class="grid grid-cols-2">
				{#if unit == 'px'}
					<div class="grid grid-cols-1">
						<Rslider
							bind:min={pxTL.min}
							bind:max={pxTL.max}
							bind:values={pxTL.values}
							label="Top-left"
						/>
						<Rslider
							bind:min={pxBL.min}
							bind:max={pxBL.max}
							bind:values={pxBL.values}
							label="Bottom-left"
						/>
					</div>
					<div class="grid grid-cols-1 grid-rows-2">
						<Rslider
							bind:min={pxTR.min}
							bind:max={pxTR.max}
							bind:values={pxTR.values}
							label="Top-right"
						/>
						<Rslider
							bind:min={pxBR.min}
							bind:max={pxBR.max}
							bind:values={pxBR.values}
							label="Bottom-right"
						/>
					</div>
				{:else}
					<div class="grid grid-cols-1">
						<Rslider
							bind:min={percentTL.min}
							bind:max={percentTL.max}
							bind:values={percentTL.values}
							label="Top-left"
						/>
						<Rslider
							bind:min={percentBL.min}
							bind:max={percentBL.max}
							bind:values={percentBL.values}
							label="Bottom-left"
						/>
					</div>
					<div class="grid grid-cols-1 grid-rows-2">
						<Rslider
							bind:min={percentTR.min}
							bind:max={percentTR.max}
							bind:values={percentTR.values}
							label="Top-right"
						/>
						<Rslider
							bind:min={percentBR.min}
							bind:max={percentBR.max}
							bind:values={percentBR.values}
							label="Bottom-right"
						/>
					</div>
				{/if}
			</div>
		{/if}
	</section>
	<section class="mt-10 flex flex-col items-center justify-center lg:mt-0">
		<div style="{borderRadiusValue};" class="mb-20 h-52 w-52 rounded-lg bg-gray-500"></div>
		<Code code={borderRadiusValue} />
	</section>
</main>

<style></style>
