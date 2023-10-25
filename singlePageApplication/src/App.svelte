<script>
  import Header from './Header.svelte'
  import Home from './Home.svelte'
  import AboutUs from './AboutUs.svelte'
  import ContactUs from './ContactUs.svelte';
  let currentPage='home'

  function changePage(x){
    currentPage=x;
    }
</script>

<header>
  <nav>
    <ul>
      <Header text='home' on:click={()=>changePage('home')} style="normal"/>
      <Header text='about us' on:click={()=>changePage('about')} style="danger"/>
      <Header text='contact' on:click={()=>changePage('contact')} style="normal"/>
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