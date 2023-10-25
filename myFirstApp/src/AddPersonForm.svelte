<script>
    import Buttons from "./Buttons.svelte";

    // this 2 belows lines just to send the form info to another file
    import {createEventDispatcher} from 'svelte'
    let dispatcherFunction=createEventDispatcher()

  
    let personName;
    let personFamily;
    let personAge;
    let personCountry;
    // let shooting=false;
    // let fighting=false
    // let sword=false
    let skills=[]
    let country

    const subForm = () =>{
        let newPerson={
          name:personName,
          family:personFamily,
          age:personAge,
          // suppose the object attribute is age nad the variable was age, i can write only age,
          // age,
          country:personCountry,
          id:Math.floor(Math.random() * 100)
        };
        dispatcherFunction('addNewPerson',newPerson)
        
      // alert(`${name} ${family} ${age} ${fighting} ${shooting} ${sword}`)
    }
</script>
<form on:submit|preventDefault={subForm}>
    <label for="name">Name</label>
    <input type="text" placeholder="name" id="name" bind:value={personName}><br>
    <label for="family">Family</label>
    <input type="text" placeholder="family" id="family" bind:value={personFamily}><br>
    <label for="age">Age</label>
    <input type="text" placeholder="age" id="age" bind:value={personAge}><br>
    <label for="">skills</label><br>
    <!-- i bind these 3 checkbox with 3 varaibles, each one takes the value of variables above -->
    <!-- by default, each one was false, when i checked, became true, so the value became true -->
    <!-- it is right, but if i have a lot and a lot of chckbox, it is not useful, so i make i bind it to a array that i create in the script section -->
    <!-- fighting <input type="checkbox" id="fighting" bind:checked={fighting}><br>
    shooting <input type="checkbox" id="shooting" bind:checked={shooting}><br>
    sword    <input type="checkbox" id="sword" bind:checked={sword}><br> -->
    fighting <input type="checkbox" id="fighting" bind:group={skills} value="fighting"><br>
    shooting <input type="checkbox" id="shooting" bind:group={skills} value="shooting"><br>
    sword    <input type="checkbox" id="sword" bind:group={skills} value="sword"><br>
    <!-- in this way when i check any checkbox, checbox value get in the array -->
    <label>Select Country</label> <br>
    <select bind:value={personCountry}>
      <option value="beirut">beirut</option>
      <option value="saida">saida</option>
      <option value="jbeil">jbeil</option>
    </select>  
    <!-- i need to submit this form info to file DisplayPerson , where the array exist -->
    <button class="btn">submit</button>
    
    <!-- i use |preventDefault to prevent refresh page after trigger -->
    <!-- preventDefault i can not use it with component <Buttons/> -->
    <!-- among Event modifier only once can be used in component -->
  </form>

  <style>
     .btn{
        padding:10px;
        color:rgb(235, 9, 9);
        outline: none;
        cursor:pointer;
        border:0px;
        text-transform: uppercase;
        font-weight: bold;
        display: block;
        margin-top: 10px;
        
    }
     label{
    width:130px;
    height:10px;
    line-height: 10px;
    border:none;
    outline: none;
    display: inline-block;
    margin-block: 10px;
  }
  input{
    padding:10px;
    border:none;
    outline:none;
    margin-block: 15px;
  }
  </style>