<script lang="ts">
	import type { IconDefinition } from '@fortawesome/fontawesome-svg-core';
	import { faLink, faChevronDown } from '@fortawesome/free-solid-svg-icons';
	import { FontAwesomeIcon } from '@fortawesome/svelte-fontawesome';
	import { slide, fade } from 'svelte/transition';
	import { quintOut } from 'svelte/easing';

	export let icon: IconDefinition = faLink;
	export let text: string = 'Default Text';
	export let isActive: boolean = false;

	// Example list of items
	let items = ['Item 1', 'Item 2', 'Item 3', 'Item 4'];

	function toggleActive() {
		isActive = !isActive;
	}
</script>

<div class="relative w-full">
	<button
		on:click={toggleActive}
		class="
			bg-surface-300
			py-1 px-2
			rounded-sm
			flex items-center justify-between
			w-full
			transition-all duration-300 ease-in-out
			hover:bg-surface-200
			hover:shadow-md
			hover:brightness-100
		"
	>
		<div class="flex items-center gap-2">
			<span><FontAwesomeIcon {icon} /></span>
			<span>{text}</span>
		</div>
		<span
			class="transform transition-transform duration-300 ease-in-out"
			class:rotate-180={isActive}
		>
			<FontAwesomeIcon icon={faChevronDown} />
		</span>
	</button>

	{#if isActive}
		<div transition:slide|local={{ duration: 300, easing: quintOut }} class="overflow-hidden">
			<ul
				transition:fade|local={{ duration: 200 }}
				class="
					w-full
					mt-1
					bg-surface-200
					rounded-sm
					shadow-md
					overflow-hidden
				"
			>
				{#each items as item}
					<li
						class="
						py-2 px-4
						hover:bg-surface-300
						cursor-pointer
						transition-colors duration-200
					"
					>
						{item}
					</li>
				{/each}
			</ul>
		</div>
	{/if}
</div>
