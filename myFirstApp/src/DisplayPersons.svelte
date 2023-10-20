<script>
import Button from './Buttons.svelte'
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

  function deletePerson(id){
  
persons = persons.filter(function(a){
 return    id!=a.id
});

// function above mean, make a filter on array persons, and return
// in an new array each person id not equal to pased id (argument) 
}

    

function openDialog(){
   let dialog=document.querySelector("dialog")
   dialog.showModal();
}


</script>

<div class="usingLoop">
{#each persons as onePerson (onePerson.id)}
<div class="person">
    <h3 class="person__id">Id : {onePerson.id}</h3>
    <h3 class="person__name">Full Name : {onePerson.name} {onePerson.family}</h3>
    <h3 class="person__age">Has {onePerson.age}</h3>
    {#if onePerson.age>30}
    <p class="person__note person__note--success">Your are accepted in fight</p>
    {:else}
    <p class="person__note person__note--failed">You are rejected from fight</p>
    {/if}
    <p>Address : {onePerson.country}</p>
    <!-- i use this way of click function (function inside function) because if 
    write on:click={deletePerson(onePerson.id)} functuion will fire with no clicking -->
    <Button type="danger" message="delete" on:click={()=>deletePerson(onePerson.id)}/>
    
</div>
{:else}
<p class="person__note person__note--normal">There is no persons to display</p>
{/each}
</div>
<Button type="normal" message="add new person" on:click={openDialog} />
<!-- <Button type="normal" message="open dialog" on:click|once={openDialog} /> -->

<style>
    .usingLoop{
        display: flex;
        gap:10px;
        align-items: center;
        flex-wrap:wrap
        
    }
    .person{
        min-width:350px;
        padding-left: 10px;
        padding-block:10px;
        box-shadow: 0px 0px 12px 2px rgba(0,0,0,0.5);
    }
    .person :is(.person__id,.person__name,.person__age){
        margin-bottom: 10px;
    }
    .person__note{
        margin:10px 0px;
        text-transform: capitalize;
        font-size:1.1rem ;
    }

    .person__note--success{
        color:green;
    }
    .person__note--failed{
        color:tomato;
    }
    .person__note--normal{
        color:lightblue;
    }
</style>

