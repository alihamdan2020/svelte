<script>
  import Li from './Li.svelte'
  import Home from './Home.svelte'
  import AboutUs from './AboutUs.svelte'
  import ContactUs from './ContactUs.svelte';

  import Fadi from './Fadi.svelte';

  let currentPage='home'
  let valueToPass="hello every one";
  let activeClass;

  function changePage(x){
    currentPage=x;    }

    function changeUpadte(e){
      valueToPass=e.detail
    }
</script>

<header>
  <nav>
    <ul>
      <Li text='home' on:click={()=>changePage('home')} style="normal"/>
      <Li text='about us' on:click={()=>changePage('about')} style="danger"/>
      <Li text='contact' on:click={()=>changePage('contact')} style="normal"/>
    </ul>
  </nav>
</header>


<div class="main">
{#if currentPage=='home'}
<Home />
{:else if currentPage=='about'}
<AboutUs />
{:else}
<ContactUs />
{/if}
</div>
<p>{currentPage}</p>

<Fadi  on:changeValue={changeUpadte}/>
<p>{valueToPass}</p>
