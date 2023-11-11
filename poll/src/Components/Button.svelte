<script>
    export let type="primary"
    export let flat=false
</script> 
<button class={type} class:flat={flat===true}>
<slot></slot>
</button>


<style>
    button {
    margin-top:20px;
    padding:10px;
    outline: none;
    border: 0;
    position: relative;
    cursor:pointer;
    left:50%;
    transform: translateX(-50%);
    color:white;
    border-radius: 5px;
    box-shadow: 1px 2px 3px  rgba(0,0,0,0.2);
}
.flat{
    box-shadow: none
}
    .primary{
        background-color: #d91b42;
        }
    .secondary{
        background-color: #45c946;
    }
</style>