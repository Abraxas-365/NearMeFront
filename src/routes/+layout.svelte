<script lang="ts">
	import '../app.postcss';
	import { AppBar } from '@skeletonlabs/skeleton';
	import { FontAwesomeIcon } from '@fortawesome/svelte-fontawesome';
	import { faBars } from '@fortawesome/free-solid-svg-icons';
	import SideBar from '$lib/components/SideBar/SideBar.svelte';

	let sidebarVisible = true;

	function toggleSidebar() {
		sidebarVisible = !sidebarVisible;
	}
</script>

<div class="flex flex-col h-screen">
	<AppBar>
		<svelte:fragment slot="lead">
			<button on:click={toggleSidebar} aria-label="Toggle Sidebar">
				<FontAwesomeIcon icon={faBars} />
			</button>
		</svelte:fragment>
		<h1 class="text-2xl">NearMe</h1>
		<svelte:fragment slot="trail">(actions)</svelte:fragment>
	</AppBar>

	<div class="flex flex-1 overflow-hidden">
		<SideBar visible={sidebarVisible} />

		<main class="flex-1 overflow-y-auto p-4">
			<slot />
		</main>
	</div>
</div>
