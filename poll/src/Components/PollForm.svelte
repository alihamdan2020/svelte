<script>
    import Button from "./Button.svelte";

    import {createEventDispatcher} from 'svelte'
    const dispatch=createEventDispatcher();

    let pollsValue={question:'',answerA:'',answerB:''}
    let errors ={question:'',answerA:'',answerB:''}

    let valid;
const submitForm=()=>{
    
    valid=true;
   if(pollsValue.question.trim().length<5){
    valid=false
    errors.question="Questions can not be empty"
   }
   else
   errors.question=''
   
   if(pollsValue.answerA.trim().length<1){
    valid=false
    errors.answerA="Answer can not be empty"
   }
   else
   errors.answerA=''
   
   if(pollsValue.answerB.trim().length<1){
    valid=false
    errors.answerB="Answer can not be empty"
   }
   else
   errors.answerB=''

   if(valid===true){
    //    this code below mean,pass this obejct {} to App.svelte 
    let polls={...pollsValue,answer1:0,answer2:0,id:Math.random()}
    dispatch('addNewPoll',polls)
   }

   
   //console.log(pollsValue)

}
</script>

<form on:submit|preventDefault={submitForm}>
    <div class="form-field">
        <label for="question">Poll Question</label>
        <input type="text" id="question" bind:value={pollsValue.question}>
        <span>{errors.question}</span>
    </div>
    <div class="form-field">
        <label for="answerA">Answer A</label>
        <input type="text" id="AnswerA" bind:value={pollsValue.answerA}>
        <span>{errors.answerA}</span>
    </div>
    <div class="form-field">
        <label for="AnswerB">Answer B</label>
        <input type="text" id="AnswerB" bind:value={pollsValue.answerB}>
        <span>{errors.answerB}</span>
    </div>
   <Button flat={false}>Add New Poll</Button>
</form>

<style>
    form{
        border:0px solid green;
        width:fit-content;
        margin:20px auto;

    }
label{
    display: block;
    margin-bottom: 2px;
}
input{
    padding:10px;
    border:1px solid #eee;
    outline: none;
    width:100%
}

.form-field{
    margin-top: 20px;
}

span{
    color:red;
    font-size: 12px;
    text-align: center;
    border:0px solid green;
    display: block;
    margin-top:5px
}
  
</style>


  