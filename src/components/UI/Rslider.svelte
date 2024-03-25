<script lang="ts">
	import RangeSlider from 'svelte-range-slider-pips';

	export let min: number = 0;
	export let max: number = 100;
	export let values: number[] = [50];
	export let label: string = 'slider';
</script>

<p class="mb-12 select-none dark:text-white">{label}</p>
<RangeSlider pips float first="label" last="label" bind:min bind:max bind:values />
