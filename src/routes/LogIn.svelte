<script>
	import { Label, Input, Button } from 'flowbite-svelte';
	import { supabase } from '$lib/supabase.js';
	import { goto } from '$app/navigation';

	let email = '';
	let password = '';

	async function signInWithEmail() {
		const { data, error } = await supabase.auth.signInWithPassword({
			email: email,
			password: password
		});
		if (data) {
			goto('/departureTimetable');
			console.log(data);
		} else error;
		console.log(error);
	}

	async function logInGitHub() {
		let session= supabase.auth.session;
		console.log("session: ", session);
		const { data, error } = await supabase.auth.signInWithOAuth({
			provider: 'github' ,
		});
	}


</script>

<div class="text-center py-11">
	<h1>Train Departure App</h1>
</div>

<div>
	<form on:submit|preventDefault={signInWithEmail} class="w-96 mx-auto">
		<div class="mb-4">
			<Label for="email">Email</Label>
			<Input class="mb-3" id="email" type="email" bind:value={email} placeholder="Email" />
		</div>

		<div class="mb-4">
			<Label for="password">Password</Label>
			<Input
				class="mb-3"
				id="password"
				type="password"
				bind:value={password}
				placeholder="Password"
			/>
		</div>

		<div class="mt-14 flex justify-center">
			<Button class="mr-1" type="submit">Log in</Button>

		</div>

		<div class="mt-12 text-sm">
			<a href="/createAccount">Create Account</a>
		</div>
		<div class="mt-2 text-sm">
			<a href="/">Forgot your password?</a>
		</div>
	</form>
	<Button type="submit" on:click={logInGitHub}>Sign In With GitHub</Button>

</div>
