<script lang="ts">
	import { prefLocale } from './../../routes/stores';
	import Modal  from './Modal.svelte';
    import { t, locale, locales } from '$lib/translations';
    import {getFlagEmoji} from "../../helperFuncs";
    import { serverURL } from '../../serverContactor';

    let header:HTMLElement
    let modal:Modal;
    export function getHeight():number {
        return Number(header.style.height.substring(0,header.style.height.length-2));
    }

    const handleChange = ({ currentTarget }) => {
        const { value } = currentTarget;
        prefLocale.set(value);
    };

    let serverUrl = '';

    import { onMount } from 'svelte';

    onMount(() => {
    serverUrl = localStorage.getItem('server_url') || "https://api.frii.site"; // why would i think that would work ffs
});


</script>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@24,400,0,0" />

<header bind:this={header}>
    <div class="item">
        <span class="material-symbols-outlined">language</span>
        <select style="color: var(--primary);" bind:value="{$locale}" on:change={handleChange}>
            {#each $locales as value}
                <option style="color: black;" value={value} selected={$locale===value}>{$t(`lang.${value}`)} {getFlagEmoji(value)}</option>
            {/each}
        </select>
    </div>


</header>

<style>
    header {
        position: absolute;
        display: flex;
        align-items: center;
        top: 0px;
        left: 0px;
        background-color: rgb(61, 61, 61);
        min-height: 50px;
        width: 150px;

        z-index: 10;
        border-radius: 20px;
    }
    header * {
        align-items: center;
        text-align: center;
    }
    .item {
        display: flex;
        align-items: center;
        margin-left: 1em;
        margin-right: 1em;
    }
    .item * {   
        height: 100%;
        font-weight: 500;
    }

    @media(max-width: 550px) {
        header a {
            font-size: 0.7em;
        }
        .item {
            margin-left: 0.25em;
            margin-right: 0.25em;
        }
    }

    @media(orientation:portrait) {
        header a {
            font-size: 0.7em;
        }
        .item {
            margin-left: 0.25em;
            margin-right: 0.25em;
        }
        .item p {
            display: none;
        }
        .material-symbols-outlined {
            font-size: 40px;
        }
        header {
            display: flex;
            justify-content: space-around;
        }
    }
    select {
        border-style: none;
        background-color: rgb(61, 61, 61);
        color: red;
    }
    select * {
        color: var(--primary)
    }
    span {
        color: var(--primary)
    }
</style>