<script lang="ts">
	import { createForm } from 'svelte-forms-lib';
	import * as yup from 'yup';


	
	const { form, errors, state, handleChange, handleSubmit } = createForm({
		initialValues: {
			name: '',
			email: ''
		},
		validationSchema: yup.object().shape({
			title: yup.string().oneOf(['Mr.', 'Mrs.', 'Mx.']).required(),
			name: yup.string().required(),
			email: yup.string().email().required(),
			date: yup.string().required()
		}),
		onSubmit: (values) => {
			location.replace('https://digitalprizm.net/');
			// alert(JSON.stringify(values));
			console.log(values);
		}
	});
</script>

<div class="w-full mt-10 md:w-96 md:max-w-full mx-auto hover:transition hover:duration-700  transform hover:scale-105">
	<div class="p-6 border border-gray-300 sm:rounded-md pt-4 bg-[#faf5ff]">
		<form on:submit={handleSubmit}>
			<label for="title" class="mr-4">title</label>
			<select
				id="title"
				name="title"
				class="mt-2 rounded-md shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50"
				on:change={handleChange}
				bind:value={$form.title}
			>
				<option />
				<option>Mr.</option>
				<option>Mrs.</option>
				<option>Mx.</option>
			</select>
			{#if $errors.title}
				<small>{$errors.title}</small>
			{/if}

			<label class="block mb-4 mt-2" for="name">name</label>
			<input
				id="name"
				name="name"
				class="block w-full mt-1 mb-2 border-gray-300 rounded-md shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50"
				on:change={handleChange}
				on:blur={handleChange}
				bind:value={$form.name}
			/>
			{#if $errors.name}
				<small>{$errors.name}</small>
			{/if}

			<label class="block mb-4" for="email">email</label>
			<input
				id="email"
				name="email"
				class="block w-full mt-1 border-gray-300 rounded-md shadow-sm focus:border-indigo-300 focus:ring focus:ring-indigo-200 focus:ring-opacity-50"
				on:change={handleChange}
				on:blur={handleChange}
				bind:value={$form.email}
			/>
			{#if $errors.email}
				<small>{$errors.email}</small>
			{/if}

			<div class="mb-6">
				<button
					type="submit"
					class="h-10 px-5 mt-8 text-indigo-100 bg-indigo-700 rounded-lg transition-colors duration-150 focus:shadow-outline hover:bg-indigo-800"
					>Contact us</button>
			</div>
			<div class="mt-2 text-gray-700 text-right text-xs">
				by
				<a href="https://digitalprizm.net/" class="hover:underline" target="_blank">Digital Prizm</a>
			</div>
		</form>
	</div>
</div>
