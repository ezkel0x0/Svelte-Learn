<script>
    let fname;
    let sname;
    let bcolor;

    export let people;
    export let additem;
    let newPerson;

    const handleSubmit = () => {
        console.log(fname,sname,bcolor);
        newPerson = {namef:fname,names:sname,belt:bcolor}
        additem(newPerson);
    }
</script>


    <form on:submit|preventDefault={handleSubmit}>
		<input type="text" placeholder="First name" bind:value={fname}>
		<input type="text" placeholder="Second Name" bind:value={sname}>
		<input type="text" placeholder="Belt Colour" bind:value={bcolor}>
		<button>Add Person</button>
	</form>

<style>

</style>