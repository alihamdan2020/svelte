<script>
import Footer from './Components/Footer.svelte';
import Header from './Components/Header.svelte'	
import Tabs from './Components/Tabs.svelte';
import PollForm from './Components/PollForm.svelte';
import AllPolls from './Components/AllPolls.svelte';
import Testimonials from './Components/Testimonials.svelte';


let testimoinals=[
	{
	id:1,
	content:"this is a best application as all",
	bloger:"fadi",
	double:true
	},
	{
	id:2,
	content:"this is a best application as all",
	bloger:"nawal"
	},
	{id:3,
	content:"this is a best application as all",
	bloger:"ahmad"
	},
	{
	id:4,
	content:"this is a best application as all",
	bloger:"samer",
	double:true
	},
	{
	id:5,
	content:"this is a best application as all",
	bloger:"samir"
	},
	{
	id:6,
	content:"this is a best application as all this is a best application as all" ,
	bloger:"manal",
	double:true
	},
	{id:7,
	content:"this is a best application",
	bloger:"ahmad"
	},
	{id:8,
	content:"this is a best application",
	bloger:"ahmad"
	},
	{id:9,
	content:"this is a best application",
	bloger:"ahmad"
	},
	{id:10,
	content:"this is a best application as all this is a best application as all",
	bloger:"ahmad",
	double:true
	},
	{id:11,
	content:"this is a best application",
	bloger:"ahmad"
	},
	{id:12,
	content:"this is a best application",
	bloger:"ahmad"
	},
	{id:13,
	content:"this is a best application",
	bloger:"ahmad"
	},

]


let items=['Current Polls','Add new poll']
let activeItem='Current Polls'

function changeActive(e){
	activeItem=e.detail
	// e.detail mean the value passed from Tabs.svelte {singleItem}
}



let polls=[{
	question:'Python or javascript',
	answerA:'python',
	answerB:'javascript',
	answer1:10,
	answer2:5,
	id:1
}]

function addVote(e){
	// the contnet of object should be same name from ApolDetaill.svelte
	let {idOfPoll,answerIs}=e.detail

	let copiedPOlls=[...polls]

	let findedPoll=copiedPOlls.find((a)=>a.id==idOfPoll)

	if(answerIs=='1'){
		findedPoll.answer1++
		console.log('add')
	}
	else{
		findedPoll.answer2++
		console.log('ommak')
	}
	
	polls=copiedPOlls
	
		

}

// i create an empty array, to add to it all object come from PolForm
function addAllPolls(e){
	let newPoll=e.detail
	polls=[newPoll,...polls]
	//activeUtem below mean, when i add the form contnet to the array, the active Item in tab return to the first tab
	//look below, what page should display when active item change
	activeItem='Current Polls'
}

// function changeActive(newValue){
// 	activeItem=newValue
// }

//all comments mean; we were able to write as traditional way. normal function pased as props
// to the Tabs compnenets, and in Tabs components we use it
</script>

<Header />
<main>
	<!-- <Tabs items={items} activeItem={activeItem} on:click={changeActive}/> -->
	<Tabs items={items} activeItem={activeItem} on:changeActiveItem={changeActive}/>
	<!--
		 <Tabs {items} {activeItem} /> 
		 if i am using props name same of variable, i can write it as line above
	-->
	{#if activeItem==='Current Polls'}
	<AllPolls {polls} on:addVote={addVote}/>
	{:else if activeItem==='Add new poll'}
	<PollForm on:addNewPoll={addAllPolls}/>
	{/if}

</main>
<Testimonials {testimoinals} />
<Footer />

<style>
	main{
		width:min(960px,100vw);
		margin:0px auto
	}
</style>