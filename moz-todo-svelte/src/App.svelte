<script>
import Button from "./Button.svelte";
import Dialog from "./Dialog.svelte";

let textContent=''

function testFunction(x){
	textContent=x;
	   let d=document.querySelector("dialog")
	    d.showModal()

	
}
</script>

<div class="main">
	<Button title="dialog 1"  on:click={()=>testFunction("slot1")} className="forSlot1"/>
	<Button title="dialog 2"  on:click={()=>testFunction("slot2")} className="forSlot2"/>
</div>

<Dialog textContent={textContent}/>
<style>

</style>