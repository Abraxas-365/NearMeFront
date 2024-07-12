<script lang="ts">
	import type { IconDefinition } from '@fortawesome/fontawesome-svg-core';
	import { faLink } from '@fortawesome/free-solid-svg-icons';
	import { FontAwesomeIcon } from '@fortawesome/svelte-fontawesome';

	export let href: string = '/';
	export let icon: IconDefinition = faLink;
	export let text: string = 'Default Text';
</script>

<a
	{href}
	class="
		bg-surface-300
		py-1 px-2
		rounded-sm
		flex items-center gap-2
		w-full
		transition-all duration-300 ease-in-out
		hover:bg-surface-200
		hover:shadow-md
		hover:brightness-100
	"
>
	<span><FontAwesomeIcon {icon} /></span>
	<span>{text}</span>
</a>
