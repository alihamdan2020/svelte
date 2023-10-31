<script>
  import {createEventDispatcher} from 'svelte'
  let dispatch=createEventDispatcher()

   // export let valueToPass="this is my job"
    

    // function jm(){
    //   test="fadi"
    //   changeUpadte(test)
     
    // }
</script>
<button on:click={()=>dispatch('changeValue','fadi2023')}>click here</button>