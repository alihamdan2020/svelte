<script>

    export let test
    export let changeUpadte

    function jm(){
      test="fadi"
      changeUpadte(test)
     
    }
</script>
<button on:click={jm}>click here</button>