<script>
 export let showModal = false;
 export let isPromo = false;
 export let message = 'default value';
</script>

{#if showModal}
<!-- svelte-ignore a11y-click-events-have-key-events -->
<div class="backdrop" class:promo={isPromo} on:click|self>
    <div class="modal">
        <slot name="title"></slot>
        <slot></slot>
    </div>
</div>
{/if}


<style>
.backdrop{
    width: 100%;
    height: 100%;
    position: fixed;
    background:rgba(0,0,0,0.8)
}

.modal{
    padding: 5px;
    border-radius: 10px;
    max-width: 500px;
    margin:5% auto;
    text-align: center;
    background: white;
}
/* .promo .model{ promo inside the modal class */

.promo .modal{
    background: crimson;
    color : white;
}

::slotted(form input),::slotted(form button){
    display:block;
    margin:10px;
}

</style>