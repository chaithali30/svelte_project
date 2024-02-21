<!-- <script>
	let name = 'svelte';
	let data;
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
	let dot = {
		title: '',
		category: '',
		content: '',
		id: null
	};
	let addNote = () => {
		const newNote = {
			id: notes.length + 1,
			title: dot.title,
			category: dot.category,
			content: dot.content
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
			title: dot.title,
			category: dot.category,
			content: dot.content,
			id: dot.id
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
	export let value = '';
	export let autofocus = false;
	export let debounce = 0;
	export let label = 'Label';
	export let hideLabel = true;
	export let id = 'search' + Math.random().toString(36);

	export let ref = null;
	export let removeFormAriaAttributes = false;
	import { createEventDispatcher, onMount, afterUpdate } from 'svelte';
	const dispatch = createEventDispatcher();
	let prevValue = value;
	let timeout = undefined;
	let calling = false;
	function debounceFn(fn) {
		if (calling) return;
		calling = true;
		timeout = setTimeout(() => {
			fn();
			calling = false;
		}, debounce);
	}
	onMount(() => {
		if (autofocus) window.requestAnimationFrame(() => ref.focus());
		return () => clearTimeout(timeout);
	});
	afterUpdate(() => {
		if (value.length > 0 && value !== prevValue) {
			if (debounce > 0) {
				debounceFn(() => dispatch('type', value));
			} else {
				dispatch('type', value);
			}
		}
		if (value.length === 0 && prevValue.length > 0) dispatch('clear');
		prevValue = value;
	});
</script> -->

<p>🎉 Hello 🎉<br />🎉 Happy New Year🎉</p>
<!-- <section>
	curd operation example
	<div class="container">
		<div class="row mt-5">
			<div class="col-md-6">
				<div class="card p-2 shadow">
					<div class="card-body">
						{#if isEdit === false}
							<h5 class="card-title mb-4">FORMS</h5>
						{:else}<h5 class="card-title mb-4 text-white bg-green-700">Edit Note</h5>{/if}
						<form>
							<div class="form-group">
								<label for="title">Title</label>
								<input
									bind:value={data.title}
									type="text"
									class="form-control"
									id="text"
									placeholder="Note Title"
								/>
							</div>
							<div class="form-group pt-4">
								<label for="category">Category</label>
								<select class="form-control" id="category" bind:value={data.category}>
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
									class="form-control"
									id="content"
									rows="2"
									placeholder="Note Content"
								/>
							</div>
							{#if isEdit === false}
								<button
									type="submit"
									on:click|preventDefault={addNote}
									class="btn btn-primary text-white bg-green-600"
								>
									Add Note
								</button>
							{:else}
								<button type="submit" on:click|preventDefault={updateNote} class="btn btn-info">
									Edit Note
								</button>
							{/if}
						</form>
					</div>
				</div>
			</div>
			<div class="col-md-6">
				{#each notes as note}
					<div class="card mb-3">
						<div class="card-header">{note.category}</div>
						<div class="card-body">
							<h5 class="card-title">{note.title}</h5>
							<p class="card-text">{note.content}</p>
							<button class="btn btn-info text-white bg-blue-700" on:click={editNote(note)}>
								Edit
							</button>
							<button class="btn btn-danger text-white bg-red-700" on:click={deleteNote(note.id)}>
								Delete
							</button>
						</div>
					</div>
				{/each}
			</div>
		</div>
	</div>
</section> -->

