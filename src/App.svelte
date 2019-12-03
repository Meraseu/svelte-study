<script>
	import ContactCard from './ContactCard.svelte';

	let name = 'Meraseudev';
	let title = '';
	let description = '';
	let image = '';
	let age = 30;

	$: uppercaseName = name.toUpperCase();

	// $: console.log(name);

	$: if (name === 'Meraseu') {
		console.log('It runs');
		age = 31;
	}

	function changeName() {
		name = 'Meraseu';
	}
</script>

<main>
	<h1>Hello {uppercaseName}! my age is {age}</h1>
	<button type="button" on:click="{ () => age += 1 }">Change Age</button>
	<!-- <button type="button" on:click="{ changeName }">Change Name</button> -->
	<!-- <input type="text" value="{ name }" on:input="{ (e) => { 
		const enterValue = e.target.value;
		name = enterValue;
	 } }"> -->
	 <input type="text" bind:value="{ name }">
	 <input type="text" bind:value="{ title }">
	 <input type="text" bind:value="{ image }">
	 <textarea name="" id="" cols="30" rows="10" bind:value="{ description }"></textarea>

	 <ContactCard 
	 	userName="{ name }"
		jobTitle="{ title }"
		{ description }
		userImage="{ image }" />
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>