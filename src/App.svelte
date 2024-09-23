<script>
	import Modal from "./Modal.svelte";
	import AddPersonForm from "./AddPersonForm.svelte";
	import AddPersonCustomEvent from "./AddPersonCustomEvent.svelte";

	export let name;
	let fname = "Kimi";
	let sname = "Raikkonen";
	let bcolor = "Black";
	let showModal = false;


	export let people = [
		{namef: 'Chuck',names:'Norris',belt:'Green',id:1},
		{namef: 'Bruce',names:'Lee',belt:'Black',id:2},
		{namef: 'Tony',names:'Jaa',belt:'Brown',id:3}
	]

	const additem = (newPerson) =>{
		people= [...people,newPerson]; //... spread operator.
		showModal = false;
	}

	$: fullname = `${fname} ${sname}`; //reactive value
	$: console.log(bcolor); //reactive statement
	$: {
		console.log(fullname); //reactive code block
	}

	const handleClick = (e,id) =>{
		people = people.filter((person)=>person.id != id); // callback function
		console.log(e); //e is optional if we need to handle events
	};
	const handleInput= (e)=>{
		fname = e.target.value;
	};
	const toggleModel=(e)=>{
		showModal = !showModal;
		console.log(e.fullname);
	}
	const addperson=(e)=>{
		people = [...people,e.detail];
		showModal = false;
	}
</script>

<Modal isPromo={true} {showModal} on:click={toggleModel}>
	<h3 slot="title">Add Person</h3>
	<!-- <AddPersonForm {people} {additem}/> -->
	 <AddPersonCustomEvent on:addperson={addperson}/>
</Modal>


<main>
	<!-- <input type="text" on:input={handleInput} value={name}>   This is a way of two way binding. Below is a simpler way of doing the same-->
	<h1>Hi {fname} !</h1>
	<p style="color:{bcolor}">{fullname} has a {bcolor} belt in Karate!</p>
	<input type="text" bind:value={fname}>
	<input type="text" bind:value={sname}>
	<input type="text" bind:value={bcolor}>

	{#each people as person (person.id)}
		<div>
			<p>{person.namef} has a <span style="color:{person.belt}">{person.belt}</span> belt</p>
			{#if person.belt=='Black'}
				<p><strong>MASTER</strong></p>
			{/if}
			<button on:click={(e)=>
				handleClick(e,person.id) 
				}>Delete</button>
		</div>
		{:else}
		<p>There are no people available!!!</p>
	{/each}
	<button on:click={toggleModel}>More</button>
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
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>