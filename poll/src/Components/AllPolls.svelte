<script>
    export let polls
    import PollDetail from "./PollDetail.svelte";
</script>

<div class="allPolls">
    {#each polls as singlePoll (singlePoll.id)}
           <PollDetail {singlePoll} on:addVote/> 
           <!-- since polldetails is a child for AllPoll not direct child for 
        App.svelteHTML, i pass the dispatch here just as name -->
    {/each}
</div>

<style>
    .allPolls{
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap:10px;
    }
  
</style>