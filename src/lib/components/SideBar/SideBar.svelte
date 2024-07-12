<script lang="ts">
	import { faHome, faUser, faGear } from '@fortawesome/free-solid-svg-icons';
	import SideBarItem from './SideBarItem.svelte';
	import { fly } from 'svelte/transition';

	export let visible: boolean = true;

	// This is your JSON configuration
	const sidebarConfig = [
		{
			ref: '/',
			icon: faHome,
			text: 'Home'
		},
		{
			icon: faUser,
			text: 'User',
			submenu: [
				{ ref: '/profile', text: 'Profile' },
				{ ref: '/settings', text: 'Settings' }
			]
		},
		{
			ref: '/settings',
			icon: faGear,
			text: 'Settings'
		}
	];
</script>

{#if visible}
	<aside
		class="bg-surface-700 w-64 p-4 overflow-y-auto"
		transition:fly={{ x: -250, duration: 300 }}
	>
		{#each sidebarConfig as item}
			<div class="mb-2">
				<SideBarItem {item} />
			</div>
		{/each}
	</aside>
{/if}
