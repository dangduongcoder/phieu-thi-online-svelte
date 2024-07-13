<script>
    export let selected = false;
    import { fade } from 'svelte/transition';

</script>

<div class="border border-solid border-red-400 rounded-full w-4 h-4 flex justify-start items-center">
    {#if selected == true}
        <div in:fade={{ duration: 500 }} out:fade={{ duration: 500 }} class="h-full w-full rounded-full bg-gray-900"></div>
    {/if}
</div>

