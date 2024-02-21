<script>
	import '../app.postcss';
	import Header from '../components/header.svelte';
	// import Button from '../components/button.svelte';
	// const handleFoo = (e) => { console.log('receive foo', e) }
	let data;
	let child = false;

	// const sidebarHandlerone = () => {
	// 	// console.log("data", id);
	// 	console.log("data");
	// }

		
</script>


<Header title="Svelte" />

<!-- on:sidebarHandler={sidebarHandlerone} -->





<slot />


