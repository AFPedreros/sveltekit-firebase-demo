<!-- <script lang="ts">
	import { createEventDispatcher } from 'svelte';
	import LucideIcon from './lucide-icon.svelte';
	import { modeCurrent, setModeUserPrefers, setModeCurrent } from '@skeletonlabs/skeleton';

	const dispatch = createEventDispatcher();

	function toggle() {
		modeCurrent.update((value) => !value);
		setModeUserPrefers($modeCurrent);
		setModeCurrent($modeCurrent);
		dispatch('toggle', $modeCurrent);
	}
</script>

<button
	type="button"
	class={`${$modeCurrent ? 'bg-surface-900' : 'bg-surface-50'} btn-icon btn-icon-sm`}
	on:click={toggle}
>
	<LucideIcon
		name={$modeCurrent ? 'Sun' : 'Moon'}
		class={`${$modeCurrent ? 'text-surface-50' : 'text-surface-900'} h-4 w-4`}
	/>
</button> -->
<script lang="ts">
	import { onMount } from 'svelte';
	import {
		modeCurrent,
		setModeUserPrefers,
		setModeCurrent,
		setInitialClassState,
		getModeOsPrefers
	} from '@skeletonlabs/skeleton';
	import LucideIcon from './lucide-icon.svelte';

	function onToggleHandler() {
		$modeCurrent = !$modeCurrent;
		setModeUserPrefers($modeCurrent);
		setModeCurrent($modeCurrent);
	}

	onMount(() => {
		if (!('modeCurrent' in localStorage)) {
			setModeCurrent(getModeOsPrefers());
		}
	});

	// State
	$: bg = $modeCurrent === true ? 'bg-surface-50' : 'bg-surface-900';
	$: thumbBg = $modeCurrent === true ? 'text-surface-900' : 'text-surface-50';
	// Reactive
	$: classesThumb = `${$modeCurrent ? 'bg-surface-900' : 'bg-surface-50'} btn-icon btn-icon-sm`;
	$: classesIcon = `${$modeCurrent ? 'text-surface-50' : 'text-surface-900'} h-4 w-4`;
</script>

<svelte:head>
	{@html `<script nonce="%sveltekit.nonce%">(${setInitialClassState.toString()})();</script>`}
</svelte:head>

<button type="button" class={classesThumb} on:click={onToggleHandler}>
	<LucideIcon name={$modeCurrent ? 'Sun' : 'Moon'} class={classesIcon} />
</button>
