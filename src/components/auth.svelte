<script lang="ts">
	let email = '';
	let password = '';
	let confirmPassword = '';

	let error = false;
	let register = false;

	function handleAuthenticate() {
		if (!email || !password || (register && !confirmPassword)) {
			error = true;
			return;
		}
	}

	function handleRegister() {
		register = !register;
	}
</script>

<div class="flex h-full w-full flex-col items-center justify-center px-8">
	<form action="" class="flex w-[350px] flex-col gap-6">
		<h1 class="h1 text-center font-bold">{register ? 'Register' : 'Login'}</h1>
		{#if error}
			<p class="text-error-600">The information you entered is not correct</p>
		{/if}
		<label class="relative">
			<p class={email ? 'above' : 'center'}>Email</p>
			<input bind:value={email} class="input" type="email" placeholder="Email" />
		</label>
		<label class="relative">
			<p class={password ? 'above' : 'center'}>Password</p>
			<input bind:value={password} class="input" type="password" placeholder="Password" />
		</label>
		{#if register}
			<label class="relative">
				<p class={confirmPassword ? 'above' : 'center'}>Confirm Password</p>
				<input
					bind:value={confirmPassword}
					class="input"
					type="password"
					placeholder="Confirm Password"
				/>
			</label>
		{/if}
		<button type="button" class="btn variant-filled-primary font-semibold">Submit</button>
	</form>
	<div class="w-[350px]">
		<hr class="mt-3 !border-t-2" />
		{#if register}
			<p class="text-center">
				Already have an account? <span
					on:click={handleRegister}
					on:keydown={() => {}}
					class="anchor cursor-pointer">Login</span
				>
			</p>
		{:else}
			<p class="text-center">
				Don't have an account? <span
					on:click={handleRegister}
					on:keydown={() => {}}
					class="anchor cursor-pointer">Register</span
				>
			</p>
		{/if}
	</div>
</div>

<style>
	.above,
	.center {
		position: absolute;
		transform: translateY(-75%);
		pointer-events: none;
		border-radius: 4px;
		padding: 0 6px;
		font-size: 0.8rem;
		z-index: 2;
	}

	.above {
		top: 0;
		left: 16px;
		background: rgba(var(--color-surface-900) / 1);
		border: 2px solid;
		border-color: rgba(var(--color-primary-700) / 1);
		font-size: 0.75rem;
	}

	.center {
		top: 50%;
		left: 6px;
		border: 1px solid transparent;
		opacity: 0;
	}
</style>
