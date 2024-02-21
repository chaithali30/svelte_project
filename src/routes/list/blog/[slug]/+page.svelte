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
		
		<div class="p-5">
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