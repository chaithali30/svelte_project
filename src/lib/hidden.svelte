<script>
    import { createEventDispatcher } from 'svelte';

    let shown = false;

    let dispatch = createEventDispatcher();

    export function show() {
    shown = !shown;
            dispatch('show', shown);
    }
</script>

<svelte:options accessors={true}/>

<!-- <button on:click={show}>Close</button> -->

{#if shown}
    <slot/>
{/if}
