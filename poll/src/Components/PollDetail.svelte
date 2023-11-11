<script>
import {createEventDispatcher} from 'svelte'
const dispatch=createEventDispatcher();

function passIdAndaswerToApp(answer,id){
dispatch('addVote',{answerIs:answer,idOfPoll:id})
}

    export let singlePoll
    // let total=singlePoll.answer1+singlePoll.answer2
    $:total=singlePoll.answer1+singlePoll.answer2
    $:firstPercentage=Math.floor((singlePoll.answer1/total)*100)
    $:secondPercentage=Math.floor((singlePoll.answer2/total)*100)
    //answer1 and answer2 tese are the total number of votes
  
    //to understand why i make $:total not as usual let total
    //if i say just let total, the totla will not increase in each click on an answer


    
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<div class="pollBox">
<h3 >{singlePoll.question}</h3>
<p>Total answers : {total}</p>
<!-- on:clik for each answer to get the id of the poll and the answer-->
<!-- what i mean is if i click on answerA i need to pass to App.svelte  2 things
first one is : id of poll
second : which answer you want to click, answer1 or answer2
when i click on answer1 (for example) the totla number for answer1 will increese by 1
NOTE: why to App.svelte, because the main Polls data (the array) exist in App.SVelte
so wee need dispatch to pass data to the parent
-->
<!-- svelte-ignore a11y-click-events-have-key-events -->
<div class="answer" on:click={()=>{passIdAndaswerToApp('1',singlePoll.id)}}>
  <div class="percent percentA" style="width:{firstPercentage}%"></div>
    <span class="anserA">{singlePoll.answerA} ({singlePoll.answer1})</span>
    <!--answerA or answerB are the answers of the polls, example  python or javascript-->
</div>
<!-- svelte-ignore a11y-click-events-have-key-events -->
<div class="answer" on:click={()=>{passIdAndaswerToApp('2',singlePoll.id)}}>
  <div class="percent percentB" style="width:{secondPercentage}%"></div>
    <span class="anserA">{singlePoll.answerB} ({singlePoll.answer2})</span>
</div>
</div>

<style>
    .pollBox{
   box-shadow: 0px 2px 4px rgba(0,0,0,0.5);
   padding: 10px;
  }
  h3{
    margin-block: 10px;
  }
  p{
    color:#808080;
    margin-top: -5px;
  }
  .answer{
    cursor: pointer;
    margin:10px 0px;
    padding:10px 10px 10px 5px;
    border-radius: 5px;
    color:#404040;
    position: relative;
    display:flex;
    align-items: center;
  }
  .percent{
    position: absolute;
    height:100%;
    left:0;
  }
  .percentA{
    background-color: rgba(255,0,0,0.3);
  }
  .percentB{
    background-color: rgba(0,255,0,0.3);
  }
  .answer:hover{
    background-color: #f2f2f2
  }
</style>