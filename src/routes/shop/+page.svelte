<script lang="ts">
	
	import { onMount } from 'svelte';

	// import Header from '../../components/header.svelte';
	// let tasks = [];
	// let response = [];
	// const url =
	// 	'https://api.spoonacular.com/recipes/complexSearch?query=pasta&maxFat=25&number=2&apiKey=5edfade8da8c40f7bef79ac4ece0af75';
	// onMount(async () => {
	// 	const res = await fetch(url);
	// 	tasks = await res.json();
	// 	response = tasks.results;
	// 	console.log(response);
	// });

	import Flatpickr from 'svelte-flatpickr';
	import 'flatpickr/dist/flatpickr.css';

	let flag = false;

	let mini = true;
	let openSidebar;
	let closeSidebar;
	let sideBar;

	onMount(() => {
		sideBar = document.getElementById('mobile-nav');
		openSidebar = document.getElementById('openSideBar');
		closeSidebar = document.getElementById('closeSideBar');
		// sideBar.style.transform = 'translateX(-260px)';

	toggleSidebar();
	});

		function sidebarHandler(flag) {
			flag=true;
			console.log("flag",flag);
			// sideBar.style.transform = 'translateX(0px)';
				openSidebar.classList.add('hidden');
				closeSidebar.classList.remove('hidden');
				
		}
		function closeHandler(flag) {
			flag=false;
			console.log("flag",flag);
			
				// sideBar.style.transform = 'translateX(-260px)';
				closeSidebar.classList.add('hidden');
				openSidebar.classList.remove('hidden');
			}
		

	function toggleSidebar() {
		if (mini) {
			console.log('closing sidebar');
			document.getElementById('mySidebar')
			document.getElementById('main')
			mini = false;
		} else {
			console.log('opening sidebar');
			document.getElementById('mySidebar')
			document.getElementById('main')
			mini = true;
		}
	}



	let value, formattedValue;
	// let  yeer;
	// let monh;
	let currentYear = new Date().getFullYear();
	console.log(currentYear);

	let isOpen = false;

	let sum;
	let ternary = false;
	// let resultt =
	//     (trinary >= true) ? "active" : "unactive";
	// console.log(resultt);

	// form create and delete
	let fid = 0;
	let fields = [{ id: fid++, description: '' }];

	const handleDelete = (id) => {
		console.log(id);
		const index = fields.indexOf(id);
		fields = [...fields.slice(0, index)];
	};
	let title = '';
	let description = '';
	const handleCreate = () => {
		const field = {
			id: fid++,
			title: title,
			description: description
		};
		fields = [field, ...fields];
		console.log('data');
	};

	// age calculator
	const options = {
		enableTime: true,
		onChange(selectedDates, dateStr) {
			console.log('flatpickr hook', selectedDates, dateStr);
		}
	};

	$: console.log({ value, formattedValue });

	function handleChange(event) {
		const [selectedDates, dateStr] = event.detail;
		console.log({ selectedDates, dateStr });
	}

	function handleSubmit(event) {
		event.preventDefault();
		const today = new Date(event.target.elements['date'].value);
		const yer = today.getFullYear();
		console.log(yer);
		console.log(event.target.elements['date'].value);

		sum = currentYear - yer;
		console.log(sum);

		if (sum >= 21) {
			alert('sucessfully');
		} else {
			alert('failure');
		}
	}

	let array: [] = [
		{
			location: 'somewhere',
			location_id: 1,
			parts: {
				part_id: 1,
				description: 'lorem jnfjvhf dhjvhjfdhv jjfdk something11',
				company: 'benzz',
				city: 'bangalor'
			}
		},
		{
			location: 'somewhere2',
			location_id: 2,
			parts: {
				part_id: 1,
				description: 'lorem jnfjvhf dhjvhjfdhv jjfdk something11',
				company: 'benzz',
				city: 'mysore'
			}
		}
	];
	// console.log('ad', array);
	// console.log(array[1].parts);
	// console.log(Object.keys(array[1].parts));

	const age = 26;
	const beverage = age >= 27 ? 'Beer' : 'Juice';
	// console.log(beverage);

	let arrayOfArray: [] = [
		{
			location: 'somewhere',
			location_id: 1,
			parts: [
				{
					part_id: 1,
					description: 'lorem jnfjvhf dhjvhjfdhv jjfdk something11'
				},
				{
					part_id: 2,
					description: 'lorem  jfbhjhdj hjvh fdjvhjdf hjd something12'
				},
				{
					part_id: 3,
					description: 'Lorem jfhfg vdfj vdbfhvbfvndbvndb m something13'
				}
			]
		},
		{
			location: 'somewhere2',
			location_id: 2,
			parts: [
				{
					part_id: 4,
					description: 'Lorem jdhvf vfgbhgbhbdnbs bh bv hfbhvjsomething22'
				},
				{
					part_id: 5,
					description: 'Lorem jh vfghbvh bchd cbbccbjn mcjnsj nc jksomething22'
				},
				{
					part_id: 6,
					description: 'Lorem jdbhbvh bdhbhjsd bhdbshbvjh b sd mnsomething23'
				}
			]
		}
	];

	const date = '2022-09-24';
	const [year, month, day] = date.split('-');
	const result = [month, day, year].join('/');

	// form
	let num = 2;
	$: formData = Array.from({ length: num }, (value) => {
		return { name: '' };
	});
	$: console.log(num, formData);
	const add = async (formData) => {};
	const handleDelete1 = (formData) => {
		console.log(formData);
		const index = fields.indexOf(formData);
	};

	let x = 0;
	const addToCounter = function () {
		++x;
	};

	// DOM event example/ Svelte window

	let btn = false;

	const openModule = (e) => {
		// console.log(e);
		btn = !btn;
	};

	const onKeydown = (e) => {
		// console.log(e);
		// btn = false;
	};

	function handleKey(event) {
		// console.log(event);
		if (event.clientX >= 1300 || event.clientY >= 200) {
			btn = false;
		}
	}

	
	// onfocus evnent example

	let isFocused = false;
	function onFocus() {
		isFocused = true;
	}

	let btnn = true;

	const openButton = (event) => {
		console.log(event);
		btnn = !btnn;
	};
</script>

<!-- sidebar -->

<div class="flex">

		<aside class="h-screen sticky top-0">
		<div
			class="h-screen sticky top-0 overflow-hidden sm:relative {mini===true ?"bg-gray-800 w-16 hidden":"bg-gray-800 w-64"} shadow md:h-full flex-col justify-between  sm:flex">
			<div class="px-8">
				<div class="h-16 w-full flex items-center">
					<svg
						aria-label="Ripples. Logo"
						role="img"
						xmlns="http://www.w3.org/2000/svg"
						width="144"
						height="30"
						viewBox="0 0 144 30"
					>
						<path
							fill="#5F7DF2"
							d="M80.544 9.48c1.177 0 2.194.306 3.053.92.86.614 1.513 1.45 1.962 2.507.448 1.058.673 2.247.673 3.568 0 1.303-.233 2.473-.699 3.51-.465 1.037-1.136 1.851-2.012 2.444-.876.592-1.885.888-3.028.888-1.405 0-2.704-.554-3.897-1.663v4.279h2.64v3.072h-9.14v-3.072h2.26V12.78H70.45V9.657h6.145v1.663l.209-.21c1.123-1.087 2.369-1.63 3.74-1.63zm17.675 0c1.176 0 2.194.306 3.053.92.859.614 1.513 1.45 1.961 2.507.449 1.058.673 2.247.673 3.568 0 1.303-.233 2.473-.698 3.51-.466 1.037-1.136 1.851-2.012 2.444-.876.592-1.886.888-3.028.888-1.405 0-2.704-.554-3.898-1.663v4.279h2.64v3.072h-9.14v-3.072h2.26V12.78h-1.904V9.657h6.144v1.663l.21-.21c1.122-1.087 2.368-1.63 3.739-1.63zM24.973 1c1.13 0 2.123.433 2.842 1.133 0 .004 0 .008.034.012 1.54 1.515 1.54 3.962-.034 5.472-.035.029-.069.058-.069.089-.719.65-1.712 1.05-2.773 1.05-.719 0-1.37.061-1.985.184-2.363.474-3.8 1.86-4.28 4.13-.114.489-.18 1.02-.2 1.59l-.003.176.001-.034.002.034c.022.505-.058 1.014-.239 1.495l-.076.182.064-.157c.106-.28.18-.575.217-.881l.008-.084-.026.195c-.286 1.797-1.858 3.188-3.754 3.282l-.204.005h-.103l-.103.002h-.034c-.65.012-1.232.072-1.78.181-2.328.473-3.765 1.863-4.279 4.139-.082.417-.142.863-.163 1.339l-.008.362v.23c0 2.02-1.603 3.681-3.661 3.861L4.16 29l-.48-.01c-.958-.073-1.849-.485-2.499-1.113-1.522-1.464-1.573-3.808-.152-5.33l.152-.154.103-.12c.719-.636 1.677-1.026 2.704-1.026.754 0 1.404-.062 2.02-.184 2.362-.475 3.8-1.86 4.28-4.126.136-.587.17-1.235.17-1.942 0-.991.411-1.896 1.027-2.583.069-.047.137-.097.172-.15.068-.051.102-.104.17-.159.633-.564 1.498-.925 2.408-.978l.229-.007h.034c.068 0 .171.003.274.009.616-.014 1.198-.074 1.746-.18 2.328-.474 3.766-1.863 4.279-4.135.082-.44.142-.912.163-1.418l.008-.385v-.132c0-2.138 1.78-3.872 4.005-3.877zm-.886 10c1.065 0 1.998.408 2.697 1.073.022.011.03.024.042.036l.025.017v.015c1.532 1.524 1.532 3.996 0 5.52-.034.03-.067.06-.067.09-.7.655-1.665 1.056-2.697 1.056-.7 0-1.332.062-1.932.186-2.298.477-3.696 1.873-4.163 4.157-.133.591-.2 1.242-.2 1.95 0 1.036-.399 1.975-1.032 2.674l-.1.084c-.676.679-1.551 1.055-2.441 1.13l-.223.012-.366-.006c-.633-.043-1.3-.254-1.865-.632-.156-.096-.296-.201-.432-.315l-.2-.177v-.012c-.734-.735-1.133-1.72-1.133-2.757 0-2.078 1.656-3.793 3.698-3.899l.198-.005h.133c.666-.007 1.266-.069 1.832-.185 2.265-.476 3.663-1.874 4.163-4.161.08-.442.139-.916.159-1.424l.008-.387v-.136c0-2.153 1.731-3.899 3.896-3.904zm3.882 11.025c1.375 1.367 1.375 3.583 0 4.95s-3.586 1.367-4.96 0c-1.345-1.367-1.345-3.583 0-4.95 1.374-1.367 3.585-1.367 4.96 0zm94.655-12.672c1.405 0 2.628.323 3.669.97 1.041.648 1.843 1.566 2.406 2.756.563 1.189.852 2.57.87 4.145h-9.954l.03.251c.132.906.476 1.633 1.03 2.18.605.596 1.386.895 2.343.895 1.058 0 2.09-.525 3.097-1.574l3.301 1.066-.203.291c-.69.947-1.524 1.67-2.501 2.166-1.075.545-2.349.818-3.821.818-1.473 0-2.774-.277-3.904-.831-1.13-.555-2.006-1.34-2.628-2.355-.622-1.016-.933-2.21-.933-3.58 0-1.354.324-2.582.971-3.682s1.523-1.961 2.628-2.583c1.104-.622 2.304-.933 3.599-.933zm13.955.126c1.202 0 2.314.216 3.339.648v-.47h3.034v3.91h-3.034l-.045-.137c-.317-.848-1.275-1.272-2.875-1.272-1.21 0-1.816.339-1.816 1.016 0 .296.161.516.483.66.321.144.791.262 1.409.355 1.735.22 3.102.536 4.1.946 1 .41 1.697.919 2.095 1.524.398.605.597 1.339.597 2.202 0 1.405-.48 2.5-1.441 3.282-.96.783-2.266 1.174-3.917 1.174-1.608 0-2.7-.321-3.275-.964V23h-3.098v-4.596h3.098l.032.187c.116.547.412.984.888 1.311.53.364 1.183.546 1.962.546.762 0 1.324-.087 1.688-.26.364-.174.546-.476.546-.908 0-.296-.076-.527-.228-.692-.153-.165-.447-.31-.883-.438-.435-.127-1.102-.27-2-.431-1.997-.313-3.433-.82-4.31-1.517-.875-.699-1.313-1.64-1.313-2.825 0-1.21.455-2.162 1.365-2.856.91-.695 2.11-1.042 3.599-1.042zm-69.164.178v10.27h1.98V23h-8.24v-3.072h2.032V12.78h-2.031V9.657h6.259zm-16.85-5.789l.37.005c1.94.05 3.473.494 4.6 1.335 1.198.892 1.797 2.185 1.797 3.878 0 1.168-.273 2.15-.819 2.945-.546.796-1.373 1.443-2.482 1.943l3.085 5.776h2.476V23h-5.827l-4.317-8.366h-2.183v5.116h2.4V23H39.646v-3.25h2.628V7.118h-2.628v-3.25h10.918zm61.329 0v16.06h1.892V23h-8.24v-3.072h2.082v-13h-2.082v-3.06h6.348zm-32.683 9.04c-.812 0-1.462.317-1.949.951-.486.635-.73 1.49-.73 2.565 0 1.007.252 1.847.756 2.52.503.673 1.161 1.01 1.974 1.01.838 0 1.481-.312 1.93-.934.448-.622.672-1.504.672-2.647 0-1.092-.228-1.942-.685-2.552-.457-.61-1.113-.914-1.968-.914zm17.675 0c-.813 0-1.463.317-1.95.951-.486.635-.73 1.49-.73 2.565 0 1.007.253 1.847.756 2.52.504.673 1.162 1.01 1.974 1.01.838 0 1.481-.312 1.93-.934.449-.622.673-1.504.673-2.647 0-1.092-.229-1.942-.686-2.552-.457-.61-1.113-.914-1.967-.914zM14.1 0C16.267 0 18 1.743 18 3.894v.01c0 2.155-1.733 3.903-3.9 3.903-4.166 0-6.3 2.133-6.3 6.293 0 2.103-1.667 3.817-3.734 3.9l-.5-.009c-.933-.075-1.8-.49-2.433-1.121C.4 16.134 0 15.143 0 14.1c0-2.144 1.733-3.903 3.9-3.903 4.166 0 6.3-2.133 6.3-6.294C10.2 1.751 11.934.005 14.1 0zm108.32 12.184c-.76 0-1.372.22-1.834.66-.46.44-.75 1.113-.87 2.018h5.561c-.118-.795-.442-1.44-.97-1.936-.53-.495-1.158-.742-1.886-.742zM49.525 7.118h-2.26v4.444h1.829c2.023 0 3.034-.754 3.034-2.26 0-.728-.233-1.274-.698-1.638-.466-.364-1.1-.546-1.905-.546zm15.821-3.593c.635 0 1.183.231 1.644.692.462.462.692 1.01.692 1.644 0 .677-.23 1.238-.692 1.682-.46.445-1.009.667-1.644.667-.643 0-1.195-.23-1.656-.692-.462-.461-.692-1.013-.692-1.657 0-.634.23-1.182.692-1.644.46-.461 1.013-.692 1.656-.692zM5.991 1.171c1.345 1.563 1.345 4.095 0 5.658-1.374 1.561-3.585 1.561-4.96 0-1.375-1.563-1.375-4.095 0-5.658 1.375-1.561 3.586-1.561 4.96 0z"
						/>
					</svg>
				</div>
				<ul class="mt-12 ">
					<li class="flex w-full justify-between text-gray-300 cursor-pointer items-center mb-6">
						<a href="/" class="flex items-center focus:outline-none focus:ring-2 focus:ring-white">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-grid mr-4"
								width="18"
								height="18"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<rect x="4" y="4" width="6" height="6" rx="1" />
								<rect x="14" y="4" width="6" height="6" rx="1" />
								<rect x="4" y="14" width="6" height="6" rx="1" />
								<rect x="14" y="14" width="6" height="6" rx="1" />
							</svg>
							<span class="text-sm ml-2 {mini===true ?"hidden":"block"} ">Dashboard</span>
						</a>
					</li>
					<li
						class="flex w-full justify-between text-gray-400 hover:text-gray-300 cursor-pointer items-center mb-6"
					>
						<a href="/" class="flex items-center focus:outline-none focus:ring-2 focus:ring-white">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-puzzle mr-4"
								width="18"
								height="18"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<path
									d="M4 7h3a1 1 0 0 0 1 -1v-1a2 2 0 0 1 4 0v1a1 1 0 0 0 1 1h3a1 1 0 0 1 1 1v3a1 1 0 0 0 1 1h1a2 2 0 0 1 0 4h-1a1 1 0 0 0 -1 1v3a1 1 0 0 1 -1 1h-3a1 1 0 0 1 -1 -1v-1a2 2 0 0 0 -4 0v1a1 1 0 0 1 -1 1h-3a1 1 0 0 1 -1 -1v-3a1 1 0 0 1 1 -1h1a2 2 0 0 0 0 -4h-1a1 1 0 0 1 -1 -1v-3a1 1 0 0 1 1 -1"
								/>
							</svg>
							<span class="text-sm ml-2 {mini===true ?"hidden":"block"}">Products</span>
						</a>
					</li>
					<li
						class="flex w-full justify-between text-gray-400 hover:text-gray-300 cursor-pointer items-center mb-6"
					>
						<a href="/" class="flex items-center focus:outline-none focus:ring-2 focus:ring-white">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-compass mr-4"
								width="18"
								height="18"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<polyline points="8 16 10 10 16 8 14 14 8 16" />
								<circle cx="12" cy="12" r="9" />
							</svg>
							<span class="text-sm ml-2 {mini===true ?"hidden":"block"}">Performance</span>
						</a>
					</li>
					<li
						class="flex w-full justify-between text-gray-400 hover:text-gray-300 cursor-pointer items-center mb-6"
					>
						<a href="/" class="flex items-center focus:outline-none focus:ring-2 focus:ring-white">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-code mr-4"
								width="20"
								height="20"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<polyline points="7 8 3 12 7 16" />
								<polyline points="17 8 21 12 17 16" />
								<line x1="14" y1="4" x2="10" y2="20" />
							</svg>
							<span class="text-sm ml-2 {mini===true ?"hidden":"block"}">Deliverables</span>
						</a>
					</li>
					<li
						class="flex w-full justify-between text-gray-400 hover:text-gray-300 cursor-pointer items-center mb-6"
					>
						<a href="/" class="flex items-center focus:outline-none focus:ring-2 focus:ring-white">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-puzzle mr-4"
								width="18"
								height="18"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<path
									d="M4 7h3a1 1 0 0 0 1 -1v-1a2 2 0 0 1 4 0v1a1 1 0 0 0 1 1h3a1 1 0 0 1 1 1v3a1 1 0 0 0 1 1h1a2 2 0 0 1 0 4h-1a1 1 0 0 0 -1 1v3a1 1 0 0 1 -1 1h-3a1 1 0 0 1 -1 -1v-1a2 2 0 0 0 -4 0v1a1 1 0 0 1 -1 1h-3a1 1 0 0 1 -1 -1v-3a1 1 0 0 1 1 -1h1a2 2 0 0 0 0 -4h-1a1 1 0 0 1 -1 -1v-3a1 1 0 0 1 1 -1"
								/>
							</svg>
							<span class="text-sm ml-2 {mini===true ?"hidden":"block"}">Invoices</span>
						</a>
					</li>
					<li
						class="flex w-full justify-between text-gray-400 hover:text-gray-300 cursor-pointer items-center mb-6"
					>
						<a href="/" class="flex items-center focus:outline-none focus:ring-2 focus:ring-white">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-stack mr-4"
								width="18"
								height="18"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<polyline points="12 4 4 8 12 12 20 8 12 4" />
								<polyline points="4 12 12 16 20 12" />
								<polyline points="4 16 12 20 20 16" />
							</svg>
							<span class="text-sm ml-2 {mini===true ?"hidden":"block"}">Inventory</span>
						</a>
					</li>
					<li
						class="flex w-full justify-between text-gray-400 hover:text-gray-300 cursor-pointer items-center"
					>
						<a href="/" class="flex items-center focus:outline-none focus:ring-2 focus:ring-white">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-settings mr-4"
								width="18"
								height="18"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<path
									d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 0 0 2.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 0 0 1.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 0 0 -1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 0 0 -2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 0 0 -2.573 -1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 0 0 -1.065 -2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 0 0 1.066 -2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z"
								/>
								<circle cx="12" cy="12" r="3" />
							</svg>
							<span class="text-sm ml-2 {mini===true ?"hidden":"block"}">Settings</span>
						</a>
					</li>
				</ul>
			</div>
			<!-- <div class="px-8 border-t border-gray-700">
				<ul class="w-full flex items-center justify-between bg-gray-800">
					<li class="cursor-pointer text-white pt-5 pb-3">
						<button
						on:click={toggleSidebar}

							aria-label="show notifications"
							class="focus:outline-none focus:ring-2 rounded focus:ring-gray-300"
						>
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-bell mr-4"
								width="20"
								height="20"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<path
									d="M10 5a2 2 0 0 1 4 0a7 7 0 0 1 4 6v3a4 4 0 0 0 2 3h-16a4 4 0 0 0 2 -3v-3a7 7 0 0 1 4 -6"
								/>
								<path d="M9 17v1a3 3 0 0 0 6 0v-1" />
							</svg>
						</button>
					</li>
				</ul>
			</div> -->
			<div class="px-4 py-4 border-t border-gray-700">
				<label class="inline-flex items-center cursor-pointer">
					<input type="checkbox" value="" class="sr-only peer" on:click={toggleSidebar}>
					<div class="relative w-11 h-6 bg-gray-200 peer-focus:outline-none peer-focus:ring-4 peer-focus:ring-blue-300 dark:peer-focus:ring-blue-800 rounded-full peer dark:bg-gray-700 peer-checked:after:translate-x-full rtl:peer-checked:after:-translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:start-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all dark:border-gray-600 peer-checked:bg-blue-600"></div>
				</label>
			</div>
		</div>
		</aside>
		<!-- mobile view -->
		<!-- <div 
			class="w-64 z-40 absolute bg-gray-800 shadow md:h-full flex-col justify-between sm:hidden transition duration-150 ease-in-out"
			id="mobile-nav">
			<div
				id="openSideBar"
				class="h-10 w-10 bg-gray-800 absolute right-0 mt-16 -mr-10 flex items-center shadow rounded-tr rounded-br justify-center cursor-pointer focus:outline-none focus:ring-2 focus:ring-offset-2 rounded focus:ring-gray-800"
				on:click={sidebarHandler}
				
			>
				<svg
					xmlns="http://www.w3.org/2000/svg"
					class="icon icon-tabler icon-tabler-adjustments"
					width="20"
					height="20"
					viewBox="0 0 24 24"
					stroke-width="1.5"
					stroke="#FFFFFF"
					fill="none"
					stroke-linecap="round"
					stroke-linejoin="round"
				>
					<path stroke="none" d="M0 0h24v24H0z" />
					<circle cx="6" cy="10" r="2" />
					<line x1="6" y1="4" x2="6" y2="8" />
					<line x1="6" y1="12" x2="6" y2="20" />
					<circle cx="12" cy="16" r="2" />
					<line x1="12" y1="4" x2="12" y2="14" />
					<line x1="12" y1="18" x2="12" y2="20" />
					<circle cx="18" cy="7" r="2" />
					<line x1="18" y1="4" x2="18" y2="5" />
					<line x1="18" y1="9" x2="18" y2="20" />
				</svg>
			</div>
			<div
				id="closeSideBar"
				class="hidden h-10 w-10 bg-gray-800 absolute right-0 mt-16 -mr-10 flex items-center shadow rounded-tr rounded-br justify-center cursor-pointer text-white"
				on:click={closeHandler}
			>
				<svg
					xmlns="http://www.w3.org/2000/svg"
					class="icon icon-tabler icon-tabler-x"
					width="20"
					height="20"
					viewBox="0 0 24 24"
					stroke-width="1.5"
					stroke="currentColor"
					fill="none"
					stroke-linecap="round"
					stroke-linejoin="round"
				>
					<path stroke="none" d="M0 0h24v24H0z" />
					<line x1="18" y1="6" x2="6" y2="18" />
					<line x1="6" y1="6" x2="18" y2="18" />
				</svg>
			</div>
			<div class="px-8">
				<div class="h-16 w-full flex items-center">
					<svg
						aria-label="Ripples. Logo"
						role="img"
						xmlns="http://www.w3.org/2000/svg"
						width="144"
						height="30"
						viewBox="0 0 144 30"
					>
						<path
							fill="#5F7DF2"
							d="M80.544 9.48c1.177 0 2.194.306 3.053.92.86.614 1.513 1.45 1.962 2.507.448 1.058.673 2.247.673 3.568 0 1.303-.233 2.473-.699 3.51-.465 1.037-1.136 1.851-2.012 2.444-.876.592-1.885.888-3.028.888-1.405 0-2.704-.554-3.897-1.663v4.279h2.64v3.072h-9.14v-3.072h2.26V12.78H70.45V9.657h6.145v1.663l.209-.21c1.123-1.087 2.369-1.63 3.74-1.63zm17.675 0c1.176 0 2.194.306 3.053.92.859.614 1.513 1.45 1.961 2.507.449 1.058.673 2.247.673 3.568 0 1.303-.233 2.473-.698 3.51-.466 1.037-1.136 1.851-2.012 2.444-.876.592-1.886.888-3.028.888-1.405 0-2.704-.554-3.898-1.663v4.279h2.64v3.072h-9.14v-3.072h2.26V12.78h-1.904V9.657h6.144v1.663l.21-.21c1.122-1.087 2.368-1.63 3.739-1.63zM24.973 1c1.13 0 2.123.433 2.842 1.133 0 .004 0 .008.034.012 1.54 1.515 1.54 3.962-.034 5.472-.035.029-.069.058-.069.089-.719.65-1.712 1.05-2.773 1.05-.719 0-1.37.061-1.985.184-2.363.474-3.8 1.86-4.28 4.13-.114.489-.18 1.02-.2 1.59l-.003.176.001-.034.002.034c.022.505-.058 1.014-.239 1.495l-.076.182.064-.157c.106-.28.18-.575.217-.881l.008-.084-.026.195c-.286 1.797-1.858 3.188-3.754 3.282l-.204.005h-.103l-.103.002h-.034c-.65.012-1.232.072-1.78.181-2.328.473-3.765 1.863-4.279 4.139-.082.417-.142.863-.163 1.339l-.008.362v.23c0 2.02-1.603 3.681-3.661 3.861L4.16 29l-.48-.01c-.958-.073-1.849-.485-2.499-1.113-1.522-1.464-1.573-3.808-.152-5.33l.152-.154.103-.12c.719-.636 1.677-1.026 2.704-1.026.754 0 1.404-.062 2.02-.184 2.362-.475 3.8-1.86 4.28-4.126.136-.587.17-1.235.17-1.942 0-.991.411-1.896 1.027-2.583.069-.047.137-.097.172-.15.068-.051.102-.104.17-.159.633-.564 1.498-.925 2.408-.978l.229-.007h.034c.068 0 .171.003.274.009.616-.014 1.198-.074 1.746-.18 2.328-.474 3.766-1.863 4.279-4.135.082-.44.142-.912.163-1.418l.008-.385v-.132c0-2.138 1.78-3.872 4.005-3.877zm-.886 10c1.065 0 1.998.408 2.697 1.073.022.011.03.024.042.036l.025.017v.015c1.532 1.524 1.532 3.996 0 5.52-.034.03-.067.06-.067.09-.7.655-1.665 1.056-2.697 1.056-.7 0-1.332.062-1.932.186-2.298.477-3.696 1.873-4.163 4.157-.133.591-.2 1.242-.2 1.95 0 1.036-.399 1.975-1.032 2.674l-.1.084c-.676.679-1.551 1.055-2.441 1.13l-.223.012-.366-.006c-.633-.043-1.3-.254-1.865-.632-.156-.096-.296-.201-.432-.315l-.2-.177v-.012c-.734-.735-1.133-1.72-1.133-2.757 0-2.078 1.656-3.793 3.698-3.899l.198-.005h.133c.666-.007 1.266-.069 1.832-.185 2.265-.476 3.663-1.874 4.163-4.161.08-.442.139-.916.159-1.424l.008-.387v-.136c0-2.153 1.731-3.899 3.896-3.904zm3.882 11.025c1.375 1.367 1.375 3.583 0 4.95s-3.586 1.367-4.96 0c-1.345-1.367-1.345-3.583 0-4.95 1.374-1.367 3.585-1.367 4.96 0zm94.655-12.672c1.405 0 2.628.323 3.669.97 1.041.648 1.843 1.566 2.406 2.756.563 1.189.852 2.57.87 4.145h-9.954l.03.251c.132.906.476 1.633 1.03 2.18.605.596 1.386.895 2.343.895 1.058 0 2.09-.525 3.097-1.574l3.301 1.066-.203.291c-.69.947-1.524 1.67-2.501 2.166-1.075.545-2.349.818-3.821.818-1.473 0-2.774-.277-3.904-.831-1.13-.555-2.006-1.34-2.628-2.355-.622-1.016-.933-2.21-.933-3.58 0-1.354.324-2.582.971-3.682s1.523-1.961 2.628-2.583c1.104-.622 2.304-.933 3.599-.933zm13.955.126c1.202 0 2.314.216 3.339.648v-.47h3.034v3.91h-3.034l-.045-.137c-.317-.848-1.275-1.272-2.875-1.272-1.21 0-1.816.339-1.816 1.016 0 .296.161.516.483.66.321.144.791.262 1.409.355 1.735.22 3.102.536 4.1.946 1 .41 1.697.919 2.095 1.524.398.605.597 1.339.597 2.202 0 1.405-.48 2.5-1.441 3.282-.96.783-2.266 1.174-3.917 1.174-1.608 0-2.7-.321-3.275-.964V23h-3.098v-4.596h3.098l.032.187c.116.547.412.984.888 1.311.53.364 1.183.546 1.962.546.762 0 1.324-.087 1.688-.26.364-.174.546-.476.546-.908 0-.296-.076-.527-.228-.692-.153-.165-.447-.31-.883-.438-.435-.127-1.102-.27-2-.431-1.997-.313-3.433-.82-4.31-1.517-.875-.699-1.313-1.64-1.313-2.825 0-1.21.455-2.162 1.365-2.856.91-.695 2.11-1.042 3.599-1.042zm-69.164.178v10.27h1.98V23h-8.24v-3.072h2.032V12.78h-2.031V9.657h6.259zm-16.85-5.789l.37.005c1.94.05 3.473.494 4.6 1.335 1.198.892 1.797 2.185 1.797 3.878 0 1.168-.273 2.15-.819 2.945-.546.796-1.373 1.443-2.482 1.943l3.085 5.776h2.476V23h-5.827l-4.317-8.366h-2.183v5.116h2.4V23H39.646v-3.25h2.628V7.118h-2.628v-3.25h10.918zm61.329 0v16.06h1.892V23h-8.24v-3.072h2.082v-13h-2.082v-3.06h6.348zm-32.683 9.04c-.812 0-1.462.317-1.949.951-.486.635-.73 1.49-.73 2.565 0 1.007.252 1.847.756 2.52.503.673 1.161 1.01 1.974 1.01.838 0 1.481-.312 1.93-.934.448-.622.672-1.504.672-2.647 0-1.092-.228-1.942-.685-2.552-.457-.61-1.113-.914-1.968-.914zm17.675 0c-.813 0-1.463.317-1.95.951-.486.635-.73 1.49-.73 2.565 0 1.007.253 1.847.756 2.52.504.673 1.162 1.01 1.974 1.01.838 0 1.481-.312 1.93-.934.449-.622.673-1.504.673-2.647 0-1.092-.229-1.942-.686-2.552-.457-.61-1.113-.914-1.967-.914zM14.1 0C16.267 0 18 1.743 18 3.894v.01c0 2.155-1.733 3.903-3.9 3.903-4.166 0-6.3 2.133-6.3 6.293 0 2.103-1.667 3.817-3.734 3.9l-.5-.009c-.933-.075-1.8-.49-2.433-1.121C.4 16.134 0 15.143 0 14.1c0-2.144 1.733-3.903 3.9-3.903 4.166 0 6.3-2.133 6.3-6.294C10.2 1.751 11.934.005 14.1 0zm108.32 12.184c-.76 0-1.372.22-1.834.66-.46.44-.75 1.113-.87 2.018h5.561c-.118-.795-.442-1.44-.97-1.936-.53-.495-1.158-.742-1.886-.742zM49.525 7.118h-2.26v4.444h1.829c2.023 0 3.034-.754 3.034-2.26 0-.728-.233-1.274-.698-1.638-.466-.364-1.1-.546-1.905-.546zm15.821-3.593c.635 0 1.183.231 1.644.692.462.462.692 1.01.692 1.644 0 .677-.23 1.238-.692 1.682-.46.445-1.009.667-1.644.667-.643 0-1.195-.23-1.656-.692-.462-.461-.692-1.013-.692-1.657 0-.634.23-1.182.692-1.644.46-.461 1.013-.692 1.656-.692zM5.991 1.171c1.345 1.563 1.345 4.095 0 5.658-1.374 1.561-3.585 1.561-4.96 0-1.375-1.563-1.375-4.095 0-5.658 1.375-1.561 3.586-1.561 4.96 0z"
						/>
					</svg>
				</div>
				<ul class="mt-12">
					<li
						class="flex w-full justify-between text-gray-300 hover:text-gray-500 cursor-pointer items-center mb-6"
					>
						<a href="#" class="flex items-center focus:outline-none focus:ring-2 focus:ring-white">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-grid"
								width="18"
								height="18"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<rect x="4" y="4" width="6" height="6" rx="1" />
								<rect x="14" y="4" width="6" height="6" rx="1" />
								<rect x="4" y="14" width="6" height="6" rx="1" />
								<rect x="14" y="14" width="6" height="6" rx="1" />
							</svg>
							<span class="text-sm ml-2">Dashboard</span>
						</a>
					</li>
					<li
						class="flex w-full justify-between text-gray-400 hover:text-gray-300 cursor-pointer items-center mb-6"
					>
						<a href="#" class="flex items-center focus:outline-none focus:ring-2 focus:ring-white">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-puzzle"
								width="18"
								height="18"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<path
									d="M4 7h3a1 1 0 0 0 1 -1v-1a2 2 0 0 1 4 0v1a1 1 0 0 0 1 1h3a1 1 0 0 1 1 1v3a1 1 0 0 0 1 1h1a2 2 0 0 1 0 4h-1a1 1 0 0 0 -1 1v3a1 1 0 0 1 -1 1h-3a1 1 0 0 1 -1 -1v-1a2 2 0 0 0 -4 0v1a1 1 0 0 1 -1 1h-3a1 1 0 0 1 -1 -1v-3a1 1 0 0 1 1 -1h1a2 2 0 0 0 0 -4h-1a1 1 0 0 1 -1 -1v-3a1 1 0 0 1 1 -1"
								/>
							</svg>
							<span class="text-sm ml-2">Products</span>
						</a>
					</li>
					<li
						class="flex w-full justify-between text-gray-400 hover:text-gray-300 cursor-pointer items-center mb-6"
					>
						<a href="#" class="flex items-center focus:outline-none focus:ring-2 focus:ring-white">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-compass"
								width="18"
								height="18"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<polyline points="8 16 10 10 16 8 14 14 8 16" />
								<circle cx="12" cy="12" r="9" />
							</svg>
							<span class="text-sm ml-2">Performance</span>
						</a>
					</li>
					<li
						class="flex w-full justify-between text-gray-400 hover:text-gray-300 cursor-pointer items-center mb-6"
					>
						<a href="#" class="flex items-center focus:outline-none focus:ring-2 focus:ring-white">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-code"
								width="20"
								height="20"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<polyline points="7 8 3 12 7 16" />
								<polyline points="17 8 21 12 17 16" />
								<line x1="14" y1="4" x2="10" y2="20" />
							</svg>
							<span class="text-sm ml-2">Deliverables</span>
						</a>
					</li>
					<li
						class="flex w-full justify-between text-gray-400 hover:text-gray-300 cursor-pointer items-center mb-6"
					>
						<a href="#" class="flex items-center focus:outline-none focus:ring-2 focus:ring-white">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-puzzle"
								width="18"
								height="18"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<path
									d="M4 7h3a1 1 0 0 0 1 -1v-1a2 2 0 0 1 4 0v1a1 1 0 0 0 1 1h3a1 1 0 0 1 1 1v3a1 1 0 0 0 1 1h1a2 2 0 0 1 0 4h-1a1 1 0 0 0 -1 1v3a1 1 0 0 1 -1 1h-3a1 1 0 0 1 -1 -1v-1a2 2 0 0 0 -4 0v1a1 1 0 0 1 -1 1h-3a1 1 0 0 1 -1 -1v-3a1 1 0 0 1 1 -1h1a2 2 0 0 0 0 -4h-1a1 1 0 0 1 -1 -1v-3a1 1 0 0 1 1 -1"
								/>
							</svg>
							<span class="text-sm ml-2">Invoices</span>
						</a>
					</li>
					<li
						class="flex w-full justify-between text-gray-400 hover:text-gray-300 cursor-pointer items-center mb-6"
					>
						<a href="#" class="flex items-center focus:outline-none focus:ring-2 focus:ring-white">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-stack"
								width="18"
								height="18"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<polyline points="12 4 4 8 12 12 20 8 12 4" />
								<polyline points="4 12 12 16 20 12" />
								<polyline points="4 16 12 20 20 16" />
							</svg>
							<span class="text-sm ml-2">Inventory</span>
						</a>
					</li>
					<li
						class="flex w-full justify-between text-gray-400 hover:text-gray-300 cursor-pointer items-center"
					>
						<a href="#" class="flex items-center focus:outline-none focus:ring-2 focus:ring-white">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-settings"
								width="18"
								height="18"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<path
									d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 0 0 2.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 0 0 1.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 0 0 -1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 0 0 -2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 0 0 -2.573 -1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 0 0 -1.065 -2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 0 0 1.066 -2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z"
								/>
								<circle cx="12" cy="12" r="3" />
							</svg>
							<span class="text-sm ml-2">Settings</span>
						</a>
					</li>
				</ul>
				<div class="flex justify-center mt-48 mb-4 w-full">
					<div class="relative">
						<div class="text-gray-300 absolute ml-4 inset-0 m-auto w-4 h-4">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-search"
								width="16"
								height="16"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<circle cx="10" cy="10" r="7" />
								<line x1="21" y1="21" x2="15" y2="15" />
							</svg>
						</div>
						<input
							class="focus:outline-none focus:ring-1 focus:ring-gray-100  rounded w-full text-sm text-gray-300 placeholder-gray-400 bg-gray-100 pl-10 py-2"
							type="text"
							placeholder="Search"
						/>
					</div>
				</div>
			</div>
			<div class="px-8 border-t border-gray-700">
				<ul class="w-full flex items-center justify-between bg-gray-800">
					<li class="cursor-pointer text-white pt-5 pb-3">
						<button
							aria-label="show notifications"
							class="focus:outline-none focus:ring-2 rounded focus:ring-gray-300"
						>
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="icon icon-tabler icon-tabler-bell"
								width="20"
								height="20"
								viewBox="0 0 24 24"
								stroke-width="1.5"
								stroke="currentColor"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<path stroke="none" d="M0 0h24v24H0z" />
								<path
									d="M10 5a2 2 0 0 1 4 0a7 7 0 0 1 4 6v3a4 4 0 0 0 2 3h-16a4 4 0 0 0 2 -3v-3a7 7 0 0 1 4 -6"
								/>
								<path d="M9 17v1a3 3 0 0 0 6 0v-1" />
							</svg>
						</button>
					</li>
					
				</ul>
			</div>
		</div> -->

<!-- main content -->
		<main>
			<div class="p-4">
				<!-- <div class="w-full h-full rounded border-dashed border-2 border-gray-300"> -->
					<!-- <main class="flex-1 mt-30 pl-4"> -->
						<div class="m-2">
							<button
								type="button"
								class="border border-collapse rounded-lg bg-purple-500 p-2"
								on:click={openModule}>Modal</button
							>
							{#if btn}
								<div
									class="container border-gray-800 border border-collapse m-2"
									on:click={onKeydown}
								>
									<a href="/">logout</a><br />
									<a href="/">Action</a><br />
									<a href="/">Something else</a>
								</div>
							{/if}
						</div>

						<input on:focus={onFocus} class="border border-collapse m-2" />
						{#if isFocused}
							<p>Input has focus</p>
						{:else}
							<p>Input does not have focus</p>
						{/if}

						<!-- age calculator -->

						<form on:submit={handleSubmit}>
							<Flatpickr
								{options}
								bind:value
								bind:formattedValue
								on:change={handleChange}
								name="date"
								class="border border-collapse m-2"
							/>

							<button type="submit"> Submit </button>
						</form>

						<!-- form create and delete -->
						<form action="" on:submit={handleCreate}>
							<div class="p-5">
								{#each fields as f}
									<input
										type="text"
										placeholder="Enter text"
										class="mx-5 rounded-lg"
										bind:value={f.title}
									/>
									<input
										type="text"
										placeholder="Enter text"
										class="mx-5 rounded-lg"
										bind:value={f.description}
									/>
									<button
										type="button"
										class="mx-5 bg-white hover:bg-gray-200 p-1 hover:outline rounded-full w-8 h-8 text-center top-5 text-lg cursor-pointer right-6"
										on:click={() => handleDelete(f.id)}>X</button
									>
								{/each}
							</div>
						</form>
						<div class="">
							<button
								type="submit"
								class="bg-blue-800 text-white rounded-lg p-3 mx-5 top-5 text-lg cursor-pointer right-6"
								on:click={() => handleCreate()}>Create</button
							>
						</div>

						<input type="number" class="bg-transparent border border-collapse m-2" bind:value={num} />

						<form action="" class="">
							{#each formData as f, index}
								<label
									>f{index + 1}
									<input
										bind:value={f.name}
										placeholder="name"
										type="text"
										class="bg-transparent border border-collapse"
									/>
								</label>
								<button
									type="button"
									class="mx-5 bg-white hover:bg-gray-200 p-1 hover:outline rounded-full w-8 h-8 text-center top-5 text-lg cursor-pointer right-6"
									on:click={() => handleDelete1(f.formData)}>X</button
								>
							{/each}
						</form>

						<!-- ternary operator example -->
						<p class="{ternary === true ? 'text-white bg-green-400' : 'text-white bg-red-400'} m-2">
							{ternary === true ? 'active' : 'inactive'}
						</p>

						{#each array as car}
							<div>{car.location}</div>
							<div>{car.location_id}</div>
							{#each Object.entries(car.parts) as [key, value]}
								<div>
									{key}{value}
									<!-- {detail.part_id}: {detail.description} -->
								</div>
							{/each}
						{/each}

						{age}

						{#each arrayOfArray as list}
							<div>{list.location}</div>
							<div>{list.location_id}</div>
							{#each list.parts as details}
								<div>{details.part_id}</div>
								<div>{details.description}</div>
							{/each}
						{/each}

						{result}
					<!-- </main> -->
				<!-- </div> -->
			</div>
		</main>
</div>
<!-- <Header /> -->
<svelte:window on:mousedown={handleKey} />
