<script>
    import logo from '../public/logo.jpg'
    import Buttons from './Buttons.svelte';

    const openDialog=()=>{
    let dialog=document.querySelector("dialog")
    dialog.showModal();
    }
</script>

<header class="header">
    <img src={logo} alt="" class="header__img">
    <nav class="header__nav">
        <ul class="header__ul">
            <li><a href="#">home</a></li>
            <li><a href="#">about us</a></li>
            <li><a href="#">contact us</a></li>
            <li class="signIn"><Buttons type="normal" message="sign in" on:click={openDialog}/></li>
        </ul>
    </nav>
</header>

<style>
    .header {
        display: flex;
        padding-block:10px;
        align-items:center;
        /* background-color: brown; */
        padding-inline: 10px;
    }
    .header__img{
        border-radius:5%
    }
    .header__nav{
        flex:1;
        /* background-color: aqua; */
    }
    
    .header__ul{
        display: flex;
        width:100%;
        /* background-color: black; */
        list-style-type: none;
        padding-left: 10px;
        gap:10px;
    }
    a{
        text-transform: uppercase;
        color: brown;
    }
    .signIn{
        margin-left:auto
    }
</style>