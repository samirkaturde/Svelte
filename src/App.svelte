<script>

	// --------------------------------------------------------------
	// Import Components
	// --------------------------------------------------------------

		import Nav from './components/Nav.svelte';
		import Model from './components/Model.svelte';
		import ShowContacts from './components/ShowContacts.svelte';

	// --------------------------------------------------------------
	// Declared variable
	// --------------------------------------------------------------

		let ModelStatus = false;
		let contacts = [];
		let message = ''

	// --------------------------------------------------------------
	// Function Definations
	// --------------------------------------------------------------

		const updatModel = () => {
			ModelStatus = !ModelStatus;
		}

		const addContact = (e) => {
			const newContact = e.detail
			contacts = [newContact, ...contacts]
			ModelStatus = !ModelStatus;
			message = 'Your contact has been added successfully'
			setTimeout(()=>{
				message = ''
			}, 3000)
		}

		const delContact = (e) => {
			const id = e.detail
			contacts = contacts.filter(contact=>contact.id !== id)
			message = 'Your contact has been deleted successfully'
			setTimeout(()=>{
				message = ''
			}, 3000)
		}
</script>

<Nav on:updatModel={updatModel}/>
<main>
	{#if message}
		<div class="alert">
			{message}
		</div>
	{/if}
	<Model {ModelStatus} on:updateModel={updatModel} on:addContact={addContact} />
	<ShowContacts {contacts} on:delContact={delContact} />
</main>

<style>
	:global(body){
		background: #edf2f7;
		padding: 0!important;
	}

	.alert {
		width : 100%;
		padding: 12px 8px;
		border-radius: 4px;
		background: linear-gradient(to right, #27ae60, #a0f305);
		color: #fff;
		margin: 10px 0;
	}

	main {
		width: 50%;
		margin: 7px auto;
	}
</style>