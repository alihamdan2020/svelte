<script>
  import Buttons from './Buttons.svelte';
  import DisplayUsers from './DisplayPersons.svelte'
  import Header from './Header.svelte'
  import Dialog from './Modal.svelte'
  import Form from './AddPersonForm.svelte'

  let persons=
    [
{id:1,name:"ali",family:"hamdan",age:45,country:"beirut"},
{id:2,name:"ahmad",family:"kazem",age:30,country:"beirut"},
{id:3,name:"ammar",family:"hakim",age:45,country:"jbeil"},
{id:4,name:"wael",family:"ramadn",age:18,country:"beirut"},
{id:5,name:"ali",family:"hamdan",age:45,country:"saida"},
{id:6,name:"ahmad",family:"kazem",age:30,country:"beirut"},
{id:7,name:"ammar",family:"hakim",age:45,country:"beirut"},
{id:8,name:"wael",family:"ramadn",age:18,country:"beirut"},
{id:9,name:"faten",family:"ozeir",age:33,country:"saida"},
{id:10,name:"samir",family:"samir",age:27,country:"jbeil"}
    ]
 
  let col="";
  // i use col in css
  let name="ali";
  let familyToChange="hamdan";
  //i create a variabel the concatinate name and family and i use
  $:fullName=`my First name is ${name} my Family is ${familyToChange}`
  function changeFamily(){
  
    familyToChange="hammoud"
   
  }

let addInfoOfNewPerson =(e) =>{
persons=[e.detail,...persons]
let dialog=document.querySelector('dialog');
    dialog.close();
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
<DisplayUsers persons={persons} />

<Dialog>
  <!-- this file is related to AddPersonForm.svelte -->
  <!-- addNewPerson should be same name of dispatcher -->
  <Form on:addNewPerson={addInfoOfNewPerson} />
  
 
</Dialog>

</div>

<style>
 
  h3{
    text-transform: uppercase;
  }
 
</style>




