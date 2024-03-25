<script lang="ts">
	import { GradientButton } from 'flowbite-svelte';
	import { Highlight } from 'svelte-highlight';
	import css from 'svelte-highlight/languages/typescript';
	import 'svelte-highlight/styles/atom-one-dark.css';
	import Swal from 'sweetalert2';
	export let code: string;

	const Toast = Swal.mixin({
		toast: true,
		position: 'top-end',
		showConfirmButton: false,
		timer: 3000,
		timerProgressBar: true,
		didOpen: (toast) => {
			toast.addEventListener('mouseenter', Swal.stopTimer);
			toast.addEventListener('mouseleave', Swal.resumeTimer);
		}
	});

	let isCopyButtonShowed: boolean = false;
	const showCopyButton = () => (isCopyButtonShowed = true);
	const removeCopyButton = () => (isCopyButtonShowed = false);

	function copyToClipboard() {
		navigator.clipboard
			.writeText(code)
			.then(() => {
				Toast.fire({
					icon: 'success',
					title: 'copied to clipboard 🤗'
				});
			})
			.catch(() => {
				Toast.fire({
					icon: 'error',
					title: 'failed to copy 👺'
				});
			});
	}
</script>

<!-- svelte-ignore a11y-no-static-element-interactions -->
<section class="relative" on:mouseenter={showCopyButton} on:mouseleave={removeCopyButton}>
	{#if isCopyButtonShowed}
		<GradientButton on:click={copyToClipboard} class="absolute  -right-4 -top-6" size="xs"
			>copy</GradientButton
		>
	{/if}
	<Highlight language={css} {code} />
</section>
