<script>
	import Button from '$lib/components/Button.svelte';
	import { page } from '$app/stores';
    
</script>

<div class="container">
    <div class="holder">
        <h1>{$page.status}</h1>
        <p>{$page.error?.message}</p>
        <x class="x"><Button on:click={()=>{window.location.href="/"}} args="fill padding">Go home</Button></x>
    </div>
</div>

<style>
    h1,p {
        opacity: 0.5;
    }
    
    .x {
        width: 50%;
        height: 4em;
        margin-top: auto;
        margin-bottom: 10px;
    }

    .container {
        display: flex;
        width: 100vw;
        height: 100vh;
        align-items: center;
        justify-content: center;
    }
    .holder {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 50vw;
        height: 50vh;
    }
    .holder h1,p {
        margin-top: 0px;
        margin-bottom: 0px;
    }
    @media(orientation:portrait) {
        .holder {
            width: 100vw;
            height: 100vh;
        }
        h1 {
            font-size: 10em;
        }
        p {
            font-size: 2em;
        }
    }
</style>