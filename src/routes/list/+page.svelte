<script lang="ts">
	import { paginate, LightPaginationNav } from 'svelte-paginate';

	import { onMount } from 'svelte';

	let item;
	let data: [] = [];
	let items: [] = [];
	let searchValue = '';
	let searchParams;
	let module = false;
	let editId;


	// pagination
	let currentPage = 1;
	let pageSize = 6;

	onMount(async () => {
		fetchData();
		// const res = await fetch(`https://dummyjson.com/products/search?q=${searchParams}`);
		// data = await res.json();
		// data = data.products;
		// items = data;
		// console.log(data);
	});

	const fetchData = async () => {
		const res = await fetch(`https://dummyjson.com/products/search?q=${searchParams || ''}`);
		data = await res.json();

		data = data.products;
		items = data;
		console.log(data);
	};

	// const photo = async () => {
	// 	const res = await fetch(`https://i.dummyjson.com/data/products/1/1.jpg`);
	// 	photos = await res.json();
	// }

	// delete method

	const onDelete = async (id) => {
		// console.log("id");
		const res = await fetch(`https://dummyjson.com/products/${id}`, {
			method: 'DELETE',
			headers: {
				'content-type': 'application/json'
			},
			body: JSON.stringify(items.id)
		});
		data = await res.json();
		// console.log('dsdasdd', items);

		if (res.status >= 200 && res.status <= 300) alert(`${data.title} Deleted succesfully`);
	};

	const closeModule = async () => {
		module = false;
	};

	//create a new

	const onCreate = async (id) => {
		module = true;

		// const res = await fetch(`https://dummyjson.com/products/${id}`, {
		// });
	};

	//update

	const onUpdate = async (id) => {
		module = true;
		editId = id;
		// console.log("hfhjgjh",editId);

		// const res = await fetch(`https://dummyjson.com/products/${id}`, {
		// 	method: 'PUT',
		// 	headers: {
		// 		'content-type': 'application/json'
		// 	},
		// 	body: JSON.stringify(id)
		// });
		// data = await res.json();
		// console.log('jhiyulk', data);
		const res = await fetch(`https://dummyjson.com/products/${editId}`);
		data = await res.json();
	};

	$: paginatedItems = paginate({ items, pageSize, currentPage });

	$: if (searchValue != '') {
		searchParams = searchValue;
		fetchData();
	}
	$: console.log(searchValue);

	// post/create module

	let postData = {
		userId: 1,
		title: 'data.little',
		content: 'data.content'
	};

	const updateNote1 = async () => {
		module = true;

		const res = await fetch(`https://dummyjson.com/products/add`, {
			method: 'POST',
			headers: {
				'content-type': 'application/json'
			},
			body: JSON.stringify({
				userID: postData.userID,
				title: postData.title,
				content: postData.content
			})
		});
		data = await res.json();
		console.log(data);
	};

	//update method

	let put = {
		// userId: 1,
		// title: 'data.little',
		// content: 'data.content'
	};

	const updateNote = async (id) => {
		module = true;
		// console.log("hghgjhkjhk",editId);

		const res = await fetch(`https://dummyjson.com/products/${editId}`, {
			method: 'PUT',
			headers: {
				'content-type': 'application/json'
			},
			body: JSON.stringify({
				userID: put.userID,
				title: put.title,
				content: put.content
			})
		});
		data = await res.json();
		// console.log('vhb', data);
	};
</script>

<!-- title -->
<div class="text-center p-2">
	<h1 class="font-bold text-4xl mb-4">Shopping Cart</h1>
</div>

<div class="flex justify-end w-full">
	<button
		class="border border-teal-500 bg-teal-500 text-white rounded-md px-4 py-2 my-2 mx-4 md:mx-16 transition duration-500 ease select-none hover:bg-teal-600 focus:outline-none focus:shadow-outline"
		on:click={onCreate}
	>
		Create</button
	>
</div>

<div class="my-2 mx-16">
	<h1 class="text-2xl font-bold">Search/Filter</h1>
	<input
		class="w-full h-12 outline-sky-600 shadow-lg my-4 p-5 shadow-neutral-200 rounded-lg border"
		type="search"
		placeholder="Search..."
		bind:value={searchValue}
	/>
</div>

<div class="mx-0 my-10 md:mx-8">
	<div class="grid grid-cols-1 md:grid-cols-3 gap-8">
		{#if paginatedItems}
			{#each paginatedItems as item}
				<div
					class="border p-5 rounded-lg hover:transition hover:duration-700  transform hover:scale-105"
				>
					<a href="list/blog/{item.id}" class="">
						<button
							class="py-2 px-4 shadow-md no-underline rounded-full bg-orange-600 text-white font-sans font-semibold text-sm border-orange-100 hover:text-white hover:bg-orange-light focus:outline-none active:shadow-none mr-2"
							>{item.id}</button
						>
						<img
							src={item.thumbnail}
							alt={item.title}
							class="h-80 w-full object-cover rounded-t-xl mt-2"
						/>
						<h5 class="text-2xl mt-2 font-bold">{item.title}</h5>
						<p class="text-lg mt-2">{item.description}</p>
						<p class="text-lg mt-2 font-bold">${item.price}</p>

						<!-- <img src={photos.images} alt={photos.title}/> -->

						{#each item.images as photos}
							<div class="grid grid-cols-1 md:grid-cols-3 gap-6">
								<img src={photos} alt={photos.title} />
							</div>
						{/each}
					</a>
					<button
						class="border border-teal-500 bg-teal-500 text-white rounded-md px-4 py-2 m-10 transition duration-500 ease select-none hover:bg-teal-600 focus:outline-none focus:shadow-outline"
						on:click={onUpdate(item.id)}
					>
						Update
					</button>
					<button
						class="border border-red-500 bg-red-500 text-white rounded-md px-4 py-2 m-2 transition duration-500 ease select-none hover:bg-red-600 focus:outline-none focus:shadow-outline"
						on:click={onDelete(item.id)}
					>
						Delete
					</button>
				</div>
			{/each}
		{/if}
	</div>
</div>
{#if module}
	<div class="relative z-10" aria-labelledby="modal-title" role="dialog" aria-modal="true">
		<div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" />

		<div class="fixed inset-0 z-10 overflow-y-auto">
			<div class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0">
				<div
					class="relative transform overflow-hidden rounded-lg bg-white px-4 pt-5 pb-4 text-left shadow-xl transition-all sm:my-8 sm:w-full sm:max-w-sm sm:p-6"
				>
					<div>
						<div class="flex h-12 w-full items-center justify-end" on:click={closeModule}>
							<svg
								xmlns="http://www.w3.org/2000/svg"
								fill="none"
								viewBox="0 0 24 24"
								strokeWidth={1.5}
								stroke="currentColor"
								class="w-6 h-6"
							>
								<path
									strokeLinecap="round"
									strokeLinejoin="round"
									d="M9.75 9.75l4.5 4.5m0-4.5l-4.5 4.5M21 12a9 9 0 11-18 0 9 9 0 0118 0z"
								/>
							</svg>
						</div>
					</div>
					<form>
						<div class="mt-3 text-center sm:mt-5">
							<div class="mt-2">
								<div class="form-group">
									<label for="title">Title</label>
									<input
										bind:value={data.title}
										type="text"
										class="form-control shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
										id="text"
										placeholder="Note Title"
									/>
								</div>

								<div class="form-group pt-4">
									<label for="content">Content</label>
									<textarea
										bind:value={data.content}
										class="form-control shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
										id="content"
										rows="2"
										placeholder="Note Content"
									/>
								</div>
							</div>
						</div>
						{#if editId}
							<button
								type="button"
								class="border border-teal-500 bg-teal-500 text-white rounded-md px-4 py-2 m-2 transition duration-500 ease select-none hover:bg-teal-600 focus:outline-none focus:shadow-outline"
								on:click={updateNote(data.id)}
							>
								Update Note
							</button>
						{:else}
							<button
								type="submit"
								class="border border-teal-500 bg-teal-500 text-white rounded-md px-4 py-2 m-2 transition duration-500 ease select-none hover:bg-teal-600 focus:outline-none focus:shadow-outline"
								on:click={updateNote1(data.id)}
							>
								Create
							</button>
						{/if}
					</form>
				</div>
			</div>
		</div>
	</div>
{/if}

<LightPaginationNav
	totalItems={items.length}
	{pageSize}
	{currentPage}
	limit={1}
	showStepOptions={true}
	on:setPage={(e) => (currentPage = e.detail.page)}
/>
