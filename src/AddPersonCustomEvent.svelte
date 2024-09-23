<script>
    import { createEventDispatcher } from "svelte";
    let dispatch = createEventDispatcher(); // used to emit a custom event from a component to parent.

    let fname;
    let sname;
    let bcolor;
    
    const handleSubmit = () =>{
        const person = {
            namef:fname,
            names:sname,
            belt:bcolor
        };
        dispatch('addperson',person);
    };
</script>

<form on:submit|preventDefault={handleSubmit}>
		<input type="text" placeholder="First name" bind:value={fname}>
		<input type="text" placeholder="Second Name" bind:value={sname}>
		<input type="text" placeholder="Belt Colour" bind:value={bcolor}>
		<button>Add Person</button>
	</form>

<style></style>