<script>
    export let title
    export let className
</script>

<button on:click class="btn {className == 'forSlot1' ? 'btnRed' : className=='forSlot2' ? 'btnGreen' : 'normal'}">{title}</button>

<style>
    .btn{
        border:none;
        outline:none;
        color:white;
        padding:10px;
        display: block;
        cursor:pointer
    }
    .btnRed{
        background-color: brown;

    }

    .btnGreen{
        background-color: chartreuse;

    }
    .normal{
        background-color: blueviolet;
    }
</style>