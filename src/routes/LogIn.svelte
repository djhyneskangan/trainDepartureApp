<script>
	import { Label, Input, Button } from 'flowbite-svelte';
</script>

<div class="text-center py-11">
	<h1>Train Departure App</h1>
</div>

<div>
	<form class="w-96 mx-auto">
		<div class="mb-4">
			<Label for="email">Email</Label>
			<Input class="mb-3" id="email" type="email" placeholder="Email" />
		</div>

		<div class="mb-4">
			<Label for="password">Password</Label>
			<Input class="mb-3" id="password" type="password" placeholder="Password" />
		</div>

		<div class="mt-14 flex justify-center">
			<Button class="mr-1" type="submit">Log in</Button>

			<Button type="submit">Sign In With GitHub</Button>
		</div>

		<div class="mt-12 text-sm">
			<a href="/createAccount">Create Account</a>
		</div>
		<div class="mt-2 text-sm">
			<a href="/">Forgot your password?</a>
		</div>
	</form>
</div>
