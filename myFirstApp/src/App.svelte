<script>
  import Buttons from './Buttons.svelte';
  import DisplayUsers from './DisplayPersons.svelte'
  import Header from './Header.svelte'
  import Dialog from './Modal.svelte'
  import Form from './AddPersonForm.svelte'


 
  let col="";
  // i use col in css
  let name="ali";
  let familyToChange="hamdan";
  //i create a variabel the concatinate name and family and i use
  $:fullName=`my First name is ${name} my Family is ${familyToChange}`
  function changeFamily(){
  
    familyToChange="hammoud"
   
  }


</script>
<div>
<Header/>  
<!-- <div class="mainDiv">
  <p>fadiiiiiiiiiiiiiii</p>
  <h1 class="testHeading">jawad hamdan 200584</h1>
  <h1 style="color:{col}" class="headinSvelte">hello every body</h1>
  <p>{fullName}</p>
  <button on:click={changeFamily}>change your family</button>
  <input type="text"  bind:value={familyToChange}>
  <hr>
  Type your favorite Color <input type="text" bind:value={col}>
  <hr>

 
</div> -->
<DisplayUsers />

<Dialog>
  
  <Form />
  
 
</Dialog>

</div>

<style>
 
  h3{
    text-transform: uppercase;
  }
 
</style>




