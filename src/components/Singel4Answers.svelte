<script>
    import Dot from "./Dot.svelte";

    export let number = 1;
    export let selected = 0;

    function chooseAnswer(number = 0) {
        if (number != selected) {
        selected = number;
        } else {
            selected = 0;
        }
    }

</script>

<div class="w-full grid grid-cols-5 select-none">
    <input type="hidden" class="a-1in4" name={`1in4-${number}`} value={selected}>
    <div class="col-span-1 text-right pr-2 text-[14px] font-bold">{number}</div>
    <button class="col-span-1 flex justify-center items-center cursor-pointer" on:click={() => {chooseAnswer(1)}}><Dot selected={selected == 1}/></button>
    <button class="col-span-1 flex justify-center items-center cursor-pointer" on:click={() => {chooseAnswer(2)}}><Dot selected={selected == 2}/></button>
    <button class="col-span-1 flex justify-center items-center cursor-pointer" on:click={() => {chooseAnswer(3)}}><Dot selected={selected == 3}/></button>
    <button class="col-span-1 flex justify-center items-center cursor-pointer" on:click={() => {chooseAnswer(4)}}><Dot selected={selected == 4}/></button>
</div>