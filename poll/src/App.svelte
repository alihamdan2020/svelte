<script>
import Footer from './Components/Footer.svelte';
import Header from './Components/Header.svelte'	
import Tabs from './Components/Tabs.svelte';
let items=['Current Polls','Add new poll']
let activeItem='Current Polls'

function changeActive(e){
	activeItem=e.detail
	// e.detail mean the value passed from Tabs.svelte {singleItem}
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
	<p>poll list</p>
	{:else if activeItem==='Add new poll'}
	<p>add new poll</p>
	{/if}

</main>
<Footer />

<style>
	main{
		width:min(960px,100vw);
		margin:0px auto
	}
</style>