<script>
    export let text
    export let style
</script>

<li>
    <a 
    href="javascript:void(0)" 
    on:click 
    class="btn {style=='normal' ? 'btnNormal' : 'btnDanger'}">
    {text}</a>
</li>

<style>
    .btn{
        text-decoration: none;
        font-size: 1.2em;
        text-transform: capitalize;
    }
    .btnNormal{
        color:green;
    }
    .btnDanger{
        color:tomato
    }
</style>