<script lang="ts">
	import { onMount } from 'svelte';
	import { page } from '$app/stores';
	let id: number;
	let datas;
	id = $page.params.slug;
	console.log(id);

	onMount(async () => {
		const res = await fetch(`https://jsonplaceholder.typicode.com/posts/${id}`);
		datas = await res.json();
		console.log(datas);
	});
</script>

<div class="w-full pt-10 md:w-96 md:max-w-full mx-auto shadow-md">
	<div class="p-6 border border-gray-300 sm:rounded-md pt-4 bg-[#c9bcd5]">
		<a href="/" class="my-6">
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
		<a href="/">
			<img
				class="w-full pt-4"
				src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ-OfgIjM7RUEFe2NkI66xdWSvjywZBTKZaIQ&usqp=CAU"
				alt=""
			/>
		</a>
		<div class="p-5">
			{#if datas}
				<p class="text-2xl">{datas.userId}</p>
				<p class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
					{datas.title}
				</p>
				<p>{datas.body}</p>
			{/if}
		</div>
		<div class="px-6 pt-4 pb-2">
			<span
				class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"
				>#work</span
			>
			<span
				class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"
				>#system</span
			>
			<span
				class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"
				>#svelte</span
			>
		</div>
	</div>
</div>
