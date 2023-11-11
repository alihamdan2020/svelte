<script>
    import { createEventDispatcher } from "svelte";

    export let testimoinals
    
</script>
<div class="testimonials">
    {#each testimoinals as testimoinal(testimoinal.id)}
        <div class="testimonial" class:type={testimoinal.double==true}>
            <i class="fa-solid fa-quote-left"></i>
            <h3>{testimoinal.bloger}</h3>
            <p>{testimoinal.content}</p>
            <p class="testimonialId">
                <span>{testimoinal.id}</span>
            </p>

        </div>
    {/each}
</div>
<style>
    .testimonials{
        width:min(960px,100vw);
		margin:100px auto;
        display: grid;
        grid-template-columns: repeat(4,1fr);  
        grid-template-rows: 120px;
        column-gap:10px;
        row-gap: 40px;
        grid-auto-flow: dense;
    }
    .testimonial{
        border:0px solid green;
        padding:10px;
        text-transform: capitalize;
        position: relative;
        z-index:0;
        background-color: #A6CF98;
        border-radius: 5px;
        color:aliceblue;
        font-family: sans-serif;
        font-weight: 300;
        
    }
    .type{
        border-color: red;
        grid-column: span 2;
    }
    .testimonialId{
        text-align: right;
        color:brown;
        position: absolute;
        top:80%;
        right:10px;
     
    }
    .testimonial h3{
        margin-bottom: 10px;
    }
    .fa-quote-left{
        color:tomato;
        font-size: 3rem;
        position:absolute;;
        top:-30px;
        z-index: -1;
        right: 10px;
        
    }
    
</style>