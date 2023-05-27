<script>
	import '@skeletonlabs/skeleton/themes/theme-crimson.css';
	import '@skeletonlabs/skeleton/styles/skeleton.css';
	import '../app.postcss';

	import { AppShell, AppBar } from '@skeletonlabs/skeleton';
	import ToggleSwitch from '../components/light-switch.svelte';
</script>

<AppShell>
	<svelte:fragment slot="header">
		<AppBar class="shadow-md">
			<svelte:fragment slot="lead">ToDo App</svelte:fragment>
			<svelte:fragment slot="trail">
				<ToggleSwitch />
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<slot />
</AppShell>
