<script>
	import { useForm, validators, HintGroup, Hint, email, required, minLength } from "svelte-use-form";

	const form = useForm();
	const formData = {
		username: '',
		password: ''
	}
	const handleSubmitForm = async (e) => {
		e.preventDefault();
		const response = await fetch('/user/login', {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json'
			},
			body: JSON.stringify(formData)
		});
		console.log(await response.json());
	};
</script>

<div>
	<h1>Login</h1>
	<form on:submit={handleSubmitForm} use:form>
		<label>
			Username
			<input type='email'
						 name='email'
						 use:validators={[required, email]}
						 bind:value={formData.username}>
			<HintGroup for="email">
				<Hint on="required">This is a mandatory field</Hint>
				<Hint on="email" hideWhenRequired>Username have to be e-mail</Hint>
			</HintGroup>
		</label>
		<label>
			Password
			<input type='password'
						 name='password'
						 autocomplete='new-password'
						 bind:value={formData.password}
						 use:validators={[required, minLength(8)]}>
			<HintGroup for="password">
				<Hint on="required">This is a mandatory field</Hint>
				<Hint on="minLength" hideWhenRequired>Password should have at least 8 characters.</Hint>
			</HintGroup>
		</label>
		<button type='submit' disabled={!$form.valid}>Login</button>
	</form>
</div>

<style>
  div {
    display: flex;
    flex-wrap: wrap;
    align-items: center;
		justify-content: center;
		padding-top: 50%;
  }
	h1 {
		width: 100%;
		text-align: center;
	}
	input, button {
		background: none;
		border: 1px solid var(--color-gray);
		color: var(--color-green);
		line-height: 1.5rem;
    margin: 0.25rem 0;
		outline: none;
	}
	button:disabled {
		color: var(--color-fg);
	}
	input {
		padding: 0 0.5rem;
	}
	label {
		display: block;
	}
</style>