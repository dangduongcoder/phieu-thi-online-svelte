<script>
    import Dot from "./Dot.svelte";


    export let number = 0;


    let number1 = '';
    let number2 = '';
    let number3 = '';
    let number4 = '';


    let row1 = [
        { selected: false },
        { selected: null },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
    ];

    let row2 = [
        { selected: null },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
    ];

    let row3 = [
        { selected: null },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
    ];

    let row4 = [
        { selected: null },
        { selected: null },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
        { selected: false },
    ];

    function chooseAnswer1(row = new Array,index = 0) {
        row1 = [
            { selected: false },
            { selected: null },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
        ];
        row1[index].selected = !row[index].selected

        if (index >= 2) {
            number1 = `${index - 2}`
        } else if (index == 0) {
            number1 = '-';
        } else if (index == 1) {
            number1 = ','
        }
    }

    function chooseAnswer2(row = new Array,index = 0) {
        row2 = [
            { selected: null },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
        ];
        row2[index].selected = !row[index].selected

        if (index >= 2) {
            number2 = `${index - 2}`
        } else if (index == 0) {
            number2 = '-';
        } else if (index == 1) {
            number2 = ','
        }
    }

    function chooseAnswer3(row = new Array,index = 0) {
        row3 = [
            { selected: null },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
        ];
        row3[index].selected = !row[index].selected

        if (index >= 2) {
            number3 = `${index - 2}`
        } else if (index == 0) {
            number3 = '-';
        } else if (index == 1) {
            number3 = ','
        }
    }

    function chooseAnswer4(row = new Array,index = 0) {
        row4 = [
            { selected: null },
            { selected: null },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
            { selected: false },
        ];
        row4[index].selected = !row[index].selected

        if (index >= 2) {
            number4 = `${index - 2}`
        } else if (index == 0) {
            number4 = '-';
        } else if (index == 1) {
            number4 = ','
        }
    }

</script>

<div class="col-span-1 p-2 flex flex-col">
    <p class="text-nowrap text-[14px] h-[18px] text-black">Câu {number}</p>
    <div class="grid grid-cols-5">
        <div class="col-span-1"></div>
        <div class="col-span-4 grid grid-cols-4">
            <div class="col-span-1 h-5 w-5 border border-solid text-black border-red-400 text-center">{number1}</div>
            <div class="col-span-1 h-5 w-5 border border-solid text-black border-red-400 text-center">{number2}</div>
            <div class="col-span-1 h-5 w-5 border border-solid text-black border-red-400 text-center">{number3}</div>
            <div class="col-span-1 h-5 w-5 border border-solid text-black border-red-400 text-center">{number4}</div>
            <input type="hidden" class="a-fill" name={`fill-${number}-1`} value={number1}>
            <input type="hidden" class="a-fill" name={`fill-${number}-2`} value={number2}>
            <input type="hidden" class="a-fill" name={`fill-${number}-3`} value={number3}>
            <input type="hidden" class="a-fill" name={`fill-${number}-4`} value={number4}>
        </div>
    </div>
    <div class="grid grid-cols-5">
        <div class="grid grid-rows-12">
            <p class="text-right pr-2 text-[14px] font-bold text-black mr-1">-</p>
            <p class="text-right pr-2 text-[14px] font-bold text-black mr-1">,</p>
            <p class="text-right pr-2 text-[14px] font-bold text-black mr-1">0</p>
            <p class="text-right pr-2 text-[14px] font-bold text-black mr-1">1</p>
            <p class="text-right pr-2 text-[14px] font-bold text-black mr-1">2</p>
            <p class="text-right pr-2 text-[14px] font-bold text-black mr-1">3</p>
            <p class="text-right pr-2 text-[14px] font-bold text-black mr-1">4</p>
            <p class="text-right pr-2 text-[14px] font-bold text-black mr-1">5</p>
            <p class="text-right pr-2 text-[14px] font-bold text-black mr-1">6</p>
            <p class="text-right pr-2 text-[14px] font-bold text-black mr-1">7</p>
            <p class="text-right pr-2 text-[14px] font-bold text-black mr-1">8</p>
            <p class="text-right pr-2 text-[14px] font-bold text-black mr-1">9</p>
        </div>

        <div class="grid grid-rows-12">
            {#each row1 as dot, index}
                {#if dot.selected != null}
                    <button class="flex justify-center items-center" on:click={() => {chooseAnswer1(row1,index)}}>
                            <Dot selected={dot.selected}/>
                    </button>
                {:else}
                    <p class="flex justify-center items-center">
                        
                    </p>
                {/if}
                
            {/each}
        </div>

        
        <div class="grid grid-rows-12">
            {#each row2 as dot, index}
                {#if dot.selected != null}
                    <button class="flex justify-center items-center" on:click={() => {chooseAnswer2(row2,index)}}>
                            <Dot selected={dot.selected}/>
                    </button>
                {:else}
                    <p class="flex justify-center items-center">
                        
                    </p>
                {/if}
                
            {/each}
        </div>

        <div class="grid grid-rows-12">
            {#each row3 as dot, index}
                {#if dot.selected != null}
                    <button class="flex justify-center items-center" on:click={() => {chooseAnswer3(row3,index)}}>
                            <Dot selected={dot.selected}/>
                    </button>
                {:else}
                    <p class="flex justify-center items-center">
                        
                    </p>
                {/if}
                
            {/each}
        </div>

        <div class="grid grid-rows-12">
            {#each row4 as dot, index}
                {#if dot.selected != null}
                    <button class="flex justify-center items-center" on:click={() => {chooseAnswer4(row4,index)}}>
                            <Dot selected={dot.selected}/>
                    </button>
                {:else}
                    <p class="flex justify-center items-center">
                        
                    </p>
                {/if}
                
            {/each}
        </div>

    </div>
</div>