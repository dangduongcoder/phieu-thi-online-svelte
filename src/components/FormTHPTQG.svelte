<script>
    import Box4Answers from "../components/Box4Answers.svelte";
    import BoxFill from "../components/BoxFill.svelte";
    import BoxYesNo from "../components/BoxYesNo.svelte";
</script>



<div class="">
    <div class="flex flex-col max-w-2xl bg-red-100 p-4 font-serif select-none rounded-2xl border border-solid border-red-200">
        <p class="font-bold mb-2">PHẦN I</p>
        <div class="grid grid-cols-2 sm:grid-cols-4 w-full gap-4">
            
            <Box4Answers from={1} to={10}/>
            <Box4Answers from={11} to={20}/>
            <Box4Answers from={21} to={30}/>
            <Box4Answers from={31} to={40}/>
            
        </div>
    
    
        <p class="font-bold mt-2 mb-2">PHẦN II</p>
        <div class="grid grid-cols-2 sm:grid-cols-4 w-full gap-4">
            <BoxYesNo first={1} second={2} />
            <BoxYesNo first={3} second={4} />
            <BoxYesNo first={5} second={6} />
            <BoxYesNo first={7} second={8} />
        </div>
    
        <p class="font-bold mt-2 mb-2">PHẦN III</p>
        <div class="grid grid-cols-1 w-full gap-4">
            <BoxFill />
        </div>
    
    </div>
</div>