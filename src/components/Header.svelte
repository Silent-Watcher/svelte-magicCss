<script lang="ts">
	import { page } from '$app/stores';
	import {
		Button,
		DarkMode,
		Mark,
		NavBrand,
		NavHamburger,
		NavLi,
		NavUl,
		Navbar
	} from 'flowbite-svelte';
	import { GithubSolid } from 'flowbite-svelte-icons';
	$: activeUrl = $page.url.pathname;
</script>

<header class="my-10 select-none text-center">
	<Navbar>
		<NavBrand href="/">
			<Mark>Magic</Mark> CSS 🧙‍♂️
		</NavBrand>
		<NavHamburger />
		<NavUl {activeUrl}>
			<NavLi href="/">Home 🏠</NavLi>
			<NavLi href="/gradient">Gradient 🔨</NavLi>
			<NavLi href="/text-shadow">text shadow</NavLi>
			<NavLi href="/border-radius">border radius</NavLi>
		</NavUl>
	</Navbar>
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
