<script>
    import Button from "./Button.svelte";

    const closeModel=function() {
        let d=document.querySelector("dialog")
        d.close()
    }

    export let textContent;
</script>

<dialog>
   
    
    {#if textContent =='slot1'}
    <h3>jawad 2021</h3>
    {:else}
    <h3>jawad 2023</h3>
    {/if}

<Button on:click={closeModel} title="close" className="forClose" /> 
</dialog>

<style>
    dialog::backdrop{
        background-color: rgba(0,0,0,0.5);
    }
</style>