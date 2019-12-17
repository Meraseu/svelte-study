<script>
	import ContactCard from "./ContactCard.svelte";

	let name = "Max";
	let title = "";
	let image = "";
	let description = "";
	let formState = 'empty';

	let createContacts = [];

	function addContact() {
		if (name.trim().length == 0 || title.trim().length == 0 || image.trim().length ==0 || description.trim().length == 0) {
			formState = 'invalid';
			return;	
		}
		formState = 'done';
		createContacts = [
			...createContacts,
			{
			id: Math.random(),
			name: name,
			jobTitle: title,
			imageUrl: image,
			desc: description
		}];
	}
	function deleteFirst() {
		createContacts = createContacts.slice(1);
	}
	function deleteLast() {
		createContacts = createContacts.slice(0, -1);
	}
</script>

<style>
	#form {
		width: 30rem;
		max-width: 100%;
		margin:1rem 0;
	}
</style>
<form id="form">
	<div class="form-control">
		<label for="userName">User Name</label>
		<input type="text" bind:value={name} id="userName" />
	</div>
	<div class="form-control">
		<label for="jobTitle">Job Title</label>
		<input type="text" bind:value={title} id="jobTitle" />
	</div>
	<div class="form-control">
		<label for="image">Image URL</label>
		<input type="text" bind:value={image} id="image" />
	</div>
	<div class="form-control">
		<label for="desc">Description</label>
		<textarea rows="3" bind:value={description} id="desc" />
	</div>
	<button on:click|preventDefault={ addContact } type="summit">Add Contact Card</button>
</form>


<button on:click={ (event) => {
	createContacts = createContacts.slice(1);
} }>Delete First</button>
<button on:click={ () => {
	createContacts = createContacts.slice(0, -1);
} }>Delete Last</button>

{#if formState == 'invalid'}
<p>Invalid Input</p>
{/if}

{#each createContacts as contact, i (contact.id)}
<h2># { i + 1 }</h2>
<ContactCard userName={contact.name} jobTitle={contact.jobTitle} description={contact.desc} userImage={contact.imageUrl} />
{:else}
	<p>Please</p>
{/each}