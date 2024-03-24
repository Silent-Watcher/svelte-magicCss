<script lang="ts">
	import { page } from '$app/stores';
	import { BottomNav, BottomNavItem } from 'flowbite-svelte';
	import {
		AdjustmentsVerticalOutline,
		HomeSolid,
		UserCircleSolid,
		WalletSolid
	} from 'flowbite-svelte-icons';
	$: activeUrl = $page.url.pathname;
</script>

<BottomNav {activeUrl} position="absolute" classInner="grid-cols-4">
	<BottomNavItem btnName="" href="/">
		<HomeSolid
			class="mb-1 h-5 w-5 text-gray-500 group-hover:text-primary-600 dark:text-gray-400 dark:group-hover:text-primary-500"
		/>
	</BottomNavItem>
	<BottomNavItem btnName="" href="/about">
		<WalletSolid
			class="mb-1 h-5 w-5 text-gray-500 group-hover:text-primary-600 dark:text-gray-400 dark:group-hover:text-primary-500"
		/>
	</BottomNavItem>
	<BottomNavItem btnName="" href="#">
		<AdjustmentsVerticalOutline
			class="mb-1 h-5 w-5 text-gray-500 group-hover:text-primary-600 dark:text-gray-400 dark:group-hover:text-primary-500"
		/>
	</BottomNavItem>
	<BottomNavItem btnName="" href="#">
		<UserCircleSolid
			class="mb-1 h-5 w-5 text-gray-500 group-hover:text-primary-600 dark:text-gray-400 dark:group-hover:text-primary-500"
		/>
	</BottomNavItem>
</BottomNav>
