<script>
	import Header from './Header.svelte';
	import Modal from './Modal.svelte';
	import CreateUserForm from './CreateUserForm.svelte';
	let showModal = false;
	const toggleModal = () => {
		showModal = !showModal;
	}
	let users = [
		{ id: 1, firstName: 'Brad', lastName: 'Burr', email: 'brabur@yahoo.com', avatarLink: ''},
		{ id: 2, firstName: 'Lindsi', lastName: 'Amussen', email: 'lindsi@yahoo.com', avatarLink: ''},
		{ id: 3, firstName: 'Kylie', lastName: 'Herrmann', email: 'kylie@yahoo.com', avatarLink: ''},
		{ id: 4, firstName: 'Jennifer', lastName: 'Burr', email: 'jenn@yahoo.com', avatarLink: ''},
		{ id: 5, firstName: 'Dave', lastName: 'Coles', email: 'dave@yahoo.com', avatarLink: ''},
	];
	const handleClick = (id) => {
		// Delete user from the users array
		users = users.filter((user) => user.id != id)
	}
	const createUser = (e) => {
		const user = e.detail;
		users = [user, ...users];
	}
</script>


<link href="https://fonts.googleapis.com/css2?family=Marcellus&display=swap" rel="stylesheet">

<Header />
<Modal isPromo={true} showModal={showModal} on:click={toggleModal} >
	<CreateUserForm on:createUser={createUser} />
	
</Modal>
<main>
	<button on:click={toggleModal}>Create User</button>
	{#each users as user (user.id)}
		<div>
			<h1>{user.firstName}</h1>
			<p>{user.lastName}</p>
			<button on:click={() => handleClick(user.id)}>Delete </button>
		</div>
	{:else}
		<p>There are no users to show...</p>
	{/each}
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
		text-transform: uppercase;
		font-size: 30px;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>