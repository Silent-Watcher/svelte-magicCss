<script lang="ts">
	import { Heading, Mark } from 'flowbite-svelte';
	import { DarkMode } from 'flowbite-svelte';
	import { Button } from 'flowbite-svelte';
	import { GithubSolid } from 'flowbite-svelte-icons';
</script>

<header class="my-10 select-none text-center">
	<Heading tag="h1" class="text-3xl">
		<Mark>Magic</Mark> CSS 🧙‍♂️
	</Heading>
</header>
<div class="grid grid-cols-1 justify-items-center">
	<section>
		<Button
			color="light"
			href=""
			class="rounded-lg bg-transparent p-2 text-xl text-gray-500 hover:bg-gray-100 dark:text-gray-400 dark:hover:bg-gray-700"
			><GithubSolid /></Button
		>
		<Button
			size="sm"
			color="light"
			href=""
			class="rounded-lg bg-transparent p-2 text-xl text-gray-500 hover:bg-gray-100 dark:text-gray-400 dark:hover:bg-gray-700"
			><DarkMode class="p-0" /></Button
		>
	</section>
</div>

<style>
</style>
