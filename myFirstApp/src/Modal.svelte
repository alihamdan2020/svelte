<script>
    import Button from "./Buttons.svelte";
    
    

function closeDialog(){
    let dialog=document.querySelector('dialog');
    dialog.close();
}
</script>

<dialog   class="dialog"> 
    <slot></slot>
    <Button message="close" type="normal" on:click={closeDialog} />
</dialog>

<style>
    .dialog{
        padding:30px;
        background-color:chocolate;
        color:wheat;
        width:400px;
        min-height:150px
    }

    .dialog::backdrop{
        background-color:rgba(0,0,0,.5)
    }
    
</style>