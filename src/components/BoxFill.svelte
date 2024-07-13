<script>
    import SingelFill from "./SingelFill.svelte";


</script>

<div class="col-span-1 h-auto border-2 border-solid border-red-400">

    <div class="flex flex-col gap-[3px]">
        <div class="w-full grid grid-cols-3 sm:grid-cols-6 text-[14px] text-red-400 font-bold divide-x-2 divide-red-400">
            
            <SingelFill number = {1}/>

            <SingelFill number = {2}/>

            <SingelFill number = {3}/>

            <SingelFill number = {4}/>

            <SingelFill number = {5}/>

            <SingelFill number = {6}/>
        </div>


    </div>
</div>
