<script>
    import Dot from "./Dot.svelte";

    export let first = 1;
    export let second = 2;

    let first_a = -1;
    let first_b = -1;
    let first_c = -1;
    let first_d = -1;

    let second_a = -1;
    let second_b = -1;
    let second_c = -1;
    let second_d = -1;

    // DIRTY CODE BUT IT WORKS WELL LMAO 


    function chooseAnswer(number = 0, order = 1, type = 1) {
        if (number == 1) {
            switch (order) {
                case 1:
                    first_a = (first_a == type) ? -1 : type;
                    break;
                case 2:
                    first_b = (first_b == type) ? -1 : type;
                    break;
                case 3:
                    first_c = (first_c == type) ? -1 : type;
                    break;
                case 4:
                    first_d = (first_d == type) ? -1 : type;
                    break;
                default:
                    break;
            }
        } else {
            switch (order) {
                case 1:
                    second_a = (second_a == type) ? -1 : type;
                    break;
                case 2:
                    second_b = (second_b == type) ? -1 : type;
                    break;
                case 3:
                    second_c = (second_c == type) ? -1 : type;
                    break;
                case 4:
                    second_d = (second_d == type) ? -1 : type;
                    break;
                default:
                    break;
            }
        }
    }


</script>

<div class="col-span-1 h-auto border-2 border-solid border-red-400">

    <div class="flex flex-col gap-[3px]">
        <div class="w-full grid grid-cols-5 text-[14px] text-black font-bold divide-x-2 divide-red-400">
            <div class="col-span-3 grid grid-cols-3 pt-2">
                <div class="col-span-1"></div>
                <div class="col-span-2 text-nowrap text-[14px] h-[18px]">Câu {first}</div>
                <div class="col-span-1 m-0 p-0 h-0 w-0"></div>
                <div class="col-span-1 text-nowrap font-medium text-[10px] text-center">Đúng</div>
                <div class="col-span-1 text-nowrap font-medium text-[10px] text-center">Sai</div>
                <div class="col-span-1 text-nowrap text-right mr-2">a)</div>
                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(1,1,1)}}><Dot selected={first_a == 1}/></button>
                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(1,1,0)}}><Dot selected={first_a == 0}/></button>
                <input type="hidden" class="a-yn" name={`yn-a-${first}`} value={first_a}>

                <div class="col-span-1 text-nowrap text-right mr-2">b)</div>
                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(1,2,1)}}><Dot selected={first_b == 1}/></button>
                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(1,2,0)}}><Dot selected={first_b == 0}/></button>
                <input type="hidden" class="a-yn" name={`yn-b-${first}`} value={first_b}>

                <div class="col-span-1 text-nowrap text-right mr-2">c)</div>
                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(1,3,1)}}><Dot selected={first_c == 1}/></button>
                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(1,3,0)}}><Dot selected={first_c == 0}/></button>
                <input type="hidden" class="a-yn" name={`yn-c-${first}`} value={first_c}>

                <div class="col-span-1 text-nowrap text-right mr-2">d)</div>
                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(1,4,1)}}><Dot selected={first_d == 1}/></button>
                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(1,4,0)}}><Dot selected={first_d == 0}/></button>
                <input type="hidden" class="a-yn" name={`yn-d-${first}`} value={first_d}>
            </div>
            <div class="col-span-2 grid grid-cols-2 pt-2">
                <div class="col-span-2 text-nowrap text-center text-[14px] max-h-[18px]">Câu {second}</div>
                <div class="col-span-1 text-nowrap font-medium text-[10px] text-center">Đúng</div>
                <div class="col-span-1 text-nowrap font-medium text-[10px] text-center">Sai</div>
                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(2,1,1)}}><Dot selected={second_a == 1}/></button>
                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(2,1,0)}}><Dot selected={second_a == 0}/></button>
                <input type="hidden" class="a-yn" name={`yn-a-${second}`} value={second_a}>

                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(2,2,1)}}><Dot selected={second_b == 1}/></button>
                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(2,2,0)}}><Dot selected={second_b == 0}/></button>
                <input type="hidden" class="a-yn" name={`yn-b-${second}`} value={second_b}>

                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(2,3,1)}}><Dot selected={second_c == 1}/></button>
                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(2,3,0)}}><Dot selected={second_c == 0}/></button>
                <input type="hidden" class="a-yn" name={`yn-c-${second}`} value={second_c}>

                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(2,4,1)}}><Dot selected={second_d == 1}/></button>
                <button class="col-span-1 text-nowrap font-medium text-[14px] flex justify-center items-center h-5" on:click={() => {chooseAnswer(2,4,0)}}><Dot selected={second_d == 0}/></button>
                <input type="hidden" class="a-yn" name={`yn-d-${second}`} value={second_d}>
            </div>
        </div>

    </div>
</div>