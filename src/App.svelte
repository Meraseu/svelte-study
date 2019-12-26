<script>
	import Header from './UI/Header.svelte';
	import MeetupGrid from './Meetups/MeetupGrid.svelte';
	import TextInput from './UI/TextInput.svelte';
	import Button from './UI/Button.svelte';

	let title = '';
	let subtitle = '';
	let address = '';
	let email = '';
	let description = '';
	let imageUrl = '';

	let meetups = [
		{
			id: 'm1',
			title: 'Coding Bootcamp',
			subtitle: 'Learn to code in 2 hours',
			description: 'In this meetup',
			imageUrl: '',
			address: 'Seoul',
			contactEmail: 'gmail.com'
		},
		{
			id: 'm2',
			title: 'Coding Bootcamp',
			subtitle: 'Learn to code in 2 hours',
			description: 'In this meetup',
			imageUrl: '',
			address: 'Seoul',
			contactEmail: 'gmail.com'
		}
	]
	function addMeetup() {
		const newMeetup = {
			id: Math.random().toString(),
			title: title,
			subtitle: subtitle,
			address: address,
			description: description,
			imageUrl: imageUrl,
			contactEmail: email
		};
		meetups = [newMeetup, ...meetups];
	}
</script>

<style>
	main {
		margin-top:5rem;
	}
	form {
		width:30rem;
		max-width:90%;
		margin:auto;
	}
</style>

<Header />

<main>
	<form on:submit|preventDefault = "{ addMeetup }">
		<TextInput 
			id="title"
			label="Title"
			value={title}
			on:input="{event => title = event.target.value}"
			type="text"
		/>
		<TextInput 
			id="subtitle"
			label="Subtitle"
			value={subtitle}
			on:input="{event => subtitle = event.target.value}"
			type="text"
		/>
		<TextInput 
			id="address"
			label="Address"
			value={address}
			on:input="{event => address = event.target.value}"
			type="text"
		/>
		<TextInput 
			id="imageUrl"
			label="ImageUrl"
			value={imageUrl}
			on:input="{event => imageUrl = event.target.value}"
			type="text"
		/>
		<TextInput 
			id="email"
			label="E-mail"
			value={email}
			on:input="{event => email = event.target.value}"
			type="text"
		/>
		<TextInput 
			id="description"
			label="Description"
			value={description}
			on:input="{event => description = event.target.value}"
			controlType="textarea"
			type="textarea"
		/>
		<Button
			type="submit"
			caption="Save"
		/>
	</form>
	<MeetupGrid meetups = { meetups } />
</main>