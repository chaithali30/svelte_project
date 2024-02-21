<script lang="ts">
	import { onMount } from 'svelte';
	import { page } from '$app/stores';
	let id: number;
	let data;
	id = $page.params.slug;
	console.log(id);

	onMount(async () => {
		const res = await fetch(`https://dummyjson.com/products/${id}`);
		data = await res.json();
		console.log(data);
	});
</script>

<div class="w-full pt-2 md:w-96 md:max-w-full mx-auto shadow-md">
	<div class="p-4 border border-gray-300 sm:rounded-md bg-[#99b3b2]">
		<a href="/list">
		<svg
		width="24" height="24"
		xmlns="http://www.w3.org/2000/svg"
		stroke="currentColor"
		viewBox="0 0 24 24"
		fill="none"
	>
		<path
			d="M19 12H5"
			stroke="#221E1F"
			stroke-width="2.5"
			stroke-linecap="round"
			stroke-linejoin="round"
		/>
		<path
			d="M12 19L5 12L12 5"
			stroke="#221E1F"
			stroke-width="2.5"
			stroke-linecap="round"
			stroke-linejoin="round"
		/>
	</svg>
	</a>
		<div class="">
			{#if data}
				<p class="text-lg mt-2">{data.id}</p>
				<p class="text-2xl mt-2">{data.brand}</p>
				<p class="mb-2 mt-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
					{data.title}
				</p>
				<p class="mb-2 text-lg tracking-tight text-gray-900 dark:text-white">{data.description}</p>
				<img class="h-80" src={data.thumbnail} alt={data.thumbnail} />
				<p class="my-2 text-lg font-semibold tracking-tight text-gray-900 dark:text-white">${data.price}</p>
				<p class="my-2 text-lg tracking-tight text-gray-900 dark:text-white">{data.discountPercentage}%</p>


			{/if}
		</div>
	</div>
</div>