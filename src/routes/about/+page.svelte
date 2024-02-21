<script>
	// form example
	import Hidden from '$lib/hidden.svelte';

	let isLogin = true;
	function loginBtn() {}
	let child;

	let name = 'svelte';

	let notes = [
		{
			id: 1,
			title: 'intro to svelt framework',
			category: 'svelte.js',
			content: 'This could be an intro to svelt,so you need to keep calm and see the magic'
		},
		{
			id: 2,
			title: 'Sweetest framework ever',
			category: 'node.js',
			content: 'This is the content of this note'
		}
	];
	let data = {
		title: '',
		category: '',
		content: '',
		id: null
	};
	let addNote = () => {
		const newNote = {
			id: notes.length + 1,
			title: data.title,
			category: data.category,
			content: data.content
		};
		notes = notes.concat(newNote);
		data = {
			id: null,
			title: '',
			category: '',
			content: ''
		};
		console.log(notes);
	};
	let deleteNote = (id) => {
		console.log(id);
		notes = notes.filter((note) => note.id !== id);
	};
	let isEdit = false;
	let editNote = (note) => {
		isEdit = true;
		data = note;
	};
	let updateNote = () => {
		isEdit = !isEdit;
		let noteDB = {
			title: data.title,
			category: data.category,
			content: data.content,
			id: data.id
		};
		let objIndex = notes.findIndex((obj) => obj.id == noteDB.id);
		console.log('Before update: ', notes[objIndex]);
		notes[objIndex] = noteDB;
		data = {
			id: null,
			title: '',
			category: '',
			content: ''
		};
	};

	// export let value = '';
	// export let autofocus = false;
	// export let debounce = 0;
	// export let ref = null;
	// import { createEventDispatcher, onMount, afterUpdate } from 'svelte';
	// const dispatch = createEventDispatcher();
	// let prevValue = value;
	// let timeout = undefined;
	// let calling = false;
	// function debounceFn(fn) {
	// 	if (calling) return;
	// 	calling = true;
	// 	timeout = setTimeout(() => {
	// 		fn();
	// 		calling = false;
	// 	}, debounce);
	// }
	// onMount(() => {
	// 	if (autofocus) window.requestAnimationFrame(() => ref.focus());
	// 	return () => clearTimeout(timeout);
	// });
	// afterUpdate(() => {
	// 	if (value.length > 0 && value !== prevValue) {
	// 		if (debounce > 0) {
	// 			debounceFn(() => dispatch('type', value));
	// 		} else {
	// 			dispatch('type', value);
	// 		}
	// 	}
	// 	if (value.length === 0 && prevValue.length > 0) dispatch('clear');
	// 	prevValue = value;
	// });
</script>

<h1 class="text-2xl font-bold text-center pt-4 pb-2">About Page</h1>
<div class="p-4">
	<div class="flex justify-end w-full">
		<button
			class="border border-teal-500 bg-teal-500 text-white rounded-md px-4 py-2 my-4 md:m-10 transition duration-500 ease select-none hover:bg-teal-600 focus:outline-none focus:shadow-outline"
			on:click={child.show}>Create</button
		>
	</div>

	<Hidden bind:this={child} on:show={(e) => (child.shown = e.detail)}>
		<div class="relative z-10" aria-labelledby="modal-title" role="dialog" aria-modal="true">
			<div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" />

			<div class="fixed inset-0 z-10 overflow-y-auto">
				<div
					class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0"
				>
					<div
						class="relative transform overflow-hidden rounded-lg bg-white px-4 pt-5 pb-4 text-left shadow-xl transition-all sm:my-8 sm:w-full sm:max-w-sm sm:p-6"
					>
						<div>
							<div class="flex h-12 w-full items-center justify-end" on:click={child.show}>
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
							<div class="mt-3 text-center sm:mt-5">
								{#if isEdit === false}
									<h5 class="card-title mb-4 p-2 text-indigo-400 font-bold text-2xl">FORMS</h5>
								{:else}<h5 class="card-title mb-4 text-white bg-green-700">Edit Note</h5>{/if}
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
										<label for="category">Category</label>
										<select
											class="form-control shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
											id="category"
											bind:value={data.category}
										>
											<option selected disabled>Selecet a category</option>
											<option value="svelte.js">svelte.js</option>
											<option value="node.js">node.js</option>
											<option value="react">react</option>
										</select>
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
						</div>
						<div class="mt-5 sm:mt-6">
							{#if isEdit === false}
								<button
									type="submit"
									on:click|preventDefault={addNote}
									class="border border-teal-500 bg-teal-500 text-white rounded-md px-4 py-2 m-2 transition duration-500 ease select-none hover:bg-teal-600 focus:outline-none focus:shadow-outline"
								>
									Add Note
								</button>
							{:else}
								<button
									type="submit"
									on:click|preventDefault={updateNote}
									class="border border-teal-500 bg-teal-500 text-white rounded-md px-4 py-2 m-2 transition duration-500 ease select-none hover:bg-teal-600 focus:outline-none focus:shadow-outline"
								>
									Edit Note
								</button>
							{/if}
						</div>
					</div>
				</div>
			</div>
		</div>
	</Hidden>
	<div class="m-0 md:m-8">
		<div class="grid grid-cols-1 md:grid-cols-3 gap-6">
			{#each notes as note}
				<div
					class="border p-5 rounded-lg hover:transition hover:duration-700  transform hover:scale-105"
				>
					<button
						class="py-2 px-4 my-2 shadow-md no-underline rounded-full bg-orange-600 text-white font-sans font-semibold text-sm border-orange-100 hover:text-white hover:bg-orange-light focus:outline-none active:shadow-none mr-2"
						>{note.category}</button
					>
					<h5 class="text-2xl mb-2 font-bold">{note.title}</h5>
					<p class="text-lg mb-2">{note.content}</p>
					<button
						on:click={child.show}
						class="border border-gray-700 bg-gray-700 text-white rounded-md px-4 py-2 m-0 md:m-2 transition duration-500 ease-in-out select-none hover:bg-gray-800 focus:outline-none focus:shadow-outline"
						on:click={editNote(note)}
					>
						Edit
					</button>
					<button
						class="border border-red-500 bg-red-500 text-white rounded-md px-4 py-2 m-0 md:m-2 transition duration-500 ease select-none hover:bg-red-600 focus:outline-none focus:shadow-outline"
						on:click={deleteNote(note.id)}
					>
						Delete
					</button>
				</div>
			{/each}
		</div>
	</div>
</div>
