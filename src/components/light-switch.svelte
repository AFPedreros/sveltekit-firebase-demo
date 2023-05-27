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

	$: classesThumb = `${$modeCurrent ? 'bg-surface-900' : 'bg-surface-50'} btn-icon btn-icon-sm`;
	$: classesIcon = `${$modeCurrent ? 'text-surface-50' : 'text-surface-900'} h-4 w-4`;
</script>

<svelte:head>
	{@html `<script nonce="%sveltekit.nonce%">(${setInitialClassState.toString()})();</script>`}
</svelte:head>

<button type="button" class={classesThumb} on:click={onToggleHandler}>
	<LucideIcon name={$modeCurrent ? 'Sun' : 'Moon'} class={classesIcon} />
</button>
