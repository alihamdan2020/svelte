<script>
    import {createEventDispatcher} from 'svelte'
    import { append } from 'svelte/internal';
    const dispatch=createEventDispatcher();

    // importance of dispatch, allow to send date from child to App

    export let activeItem
    export let items
   
   // export let changeActive
    // function changeActiveItem(itemValue){
    //     changeActive(itemValue)
    // }
 
</script>

<div class="tabs">
<ul>
    {#each items as singleItem}
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <!-- becode below mean pass the activeitem by clikck to append.svelte -->
        <li on:click={()=>dispatch('changeActiveItem',singleItem)}>
            
        <!-- 
        can we make the following
        <li on:click={()=>changeActiveItem(singleItem)}> 
        -->
        
        <!-- apply class named active if condition is true -->
        <div 
        class:active={singleItem==activeItem}>
        {singleItem}
        </div>   
        <!-- above line mean,the active one, where single item equal props activeItem  -->
        </li>
    {/each}
</ul>
</div>

<style>
    .tabs{
        margin:40px 0px
    }
   .active{
    color:#d91b42;
    border-bottom: 2px solid #d91b42;
    padding-bottom: 8px;
   }
   ul{
    display: flex;
    justify-content: center;
    gap:40px;
   }
   li{
    font-size:18px;
    cursor: pointer;
    }
</style>