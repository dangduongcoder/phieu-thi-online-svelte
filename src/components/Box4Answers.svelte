<script>
    import Singel4Answers from "./Singel4Answers.svelte";


	export let from;
    export let to;
</script>

<div class="col-span-1 h-auto border-2 border-solid border-red-400 p-2">

    <div class="flex flex-col gap-[3px]">
        <div class="w-full grid grid-cols-5 text-[14px] text-red-400 font-bold">
            <div class="col-span-1"></div>
            <div class="col-span-1 flex justify-center items-center">A</div>
            <div class="col-span-1 flex justify-center items-center">B</div>
            <div class="col-span-1 flex justify-center items-center">C</div>
            <div class="col-span-1 flex justify-center items-center">D</div>
        </div>
        
        {#each Array(to - from + 1) as _, i}
            <Singel4Answers number = {from + i}/>
        {/each}

    </div>
</div>
