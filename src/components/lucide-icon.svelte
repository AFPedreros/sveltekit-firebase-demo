<script lang="ts">
	import * as icons from 'lucide-svelte';
	type IconName = 'Sun' | 'Moon' | 'Save';
	export let name: IconName;
</script>

<svelte:component this={icons[name]} {...$$props} />
