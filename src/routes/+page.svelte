<script lang="ts">
	import { paginate, LightPaginationNav } from 'svelte-paginate';

	import { onMount } from 'svelte';
	let datas;
	let items: [] = [];

	// pagination
	let currentPage = 1;
	let pageSize = 4;
	$: paginatedItems = paginate({ items, pageSize, currentPage });

	// api fetching
	onMount(async () => {
		const res = await fetch('https://jsonplaceholder.typicode.com/posts');
		datas = await res.json();
		// console.log(datas);

		items = datas.map((x: [] = []) => {
			datas = x;
			return x;
		});
	});
</script>

<div class="container mx-auto m-10">
	<h1
		class="font-bold text-3xl pb-6 text-transparent bg-clip-text bg-gradient-to-r from-purple-700 to-red-600"
	>
		Posts
	</h1>
	<div class="grid gap-6 grid-cols-1 md:grid-cols-2 md:m-2">
		{#if paginatedItems}
			{#each paginatedItems as item}
				<div
					class="p-10 bg-white hover:bg-gray-100 border-solid border rounded-md hover:transition hover:duration-700  transform hover:scale-105"
				>
					<h1 class="text-2xl font-bold">{item.id}</h1>
					<p class="text-2xl mb-4">{item.title}</p>
					<a
						href="details/{item.id}"
						class="py-2 px-4 shadow-md no-underline rounded-full bg-orange-600 text-white font-sans font-semibold text-sm border-orange-100 hover:text-white hover:bg-orange-light focus:outline-none active:shadow-none mr-2"
						>read more</a
					>
				</div>
			{/each}
		{/if}
	</div>
</div>

<LightPaginationNav
	totalItems={items.length}
	{pageSize}
	{currentPage}
	limit={1}
	showStepOptions={true}
	on:setPage={(e) => (currentPage = e.detail.page)}
/>
