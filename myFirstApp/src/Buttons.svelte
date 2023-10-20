<script>

    export let message;
    export let type;
   

 
</script>
<button on:click class="btn {type === 'danger' ? 'red' : type === 'success' ? 'green' : 'normal'} posit">{message}</button>
<style>
    .btn{
        padding:10px;
        color:white;
        outline: none;
        cursor:pointer;
        border:0px;
        text-transform: uppercase;
        font-weight: bold;
    }
    .red{
        background-color: brown;
    }
    .green{
        background-color: chartreuse;
    }
    .normal{
        background-color: #eee;
        color:violet;
        margin-top: 10px;
    }
    
</style>