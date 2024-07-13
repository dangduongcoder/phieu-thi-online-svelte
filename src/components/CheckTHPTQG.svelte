<script>

    import { Badge, Button, Toast, Modal } from "flowbite-svelte";

    let showModal = false;


    let mark = 0;

    let corrects = [
        [],
        [],
        []
    ]

    let dapan1in4s = [
        [1, false],
        [2, false],
        [3, false],
        [1, false],
        [2, false],
        [4, false],
        [1, false],
        [2, false],
        [4, false],
        [2, false],
        [1, false],
        [4, false],
    ]

    let dapanyesnos  = [
        [
            [1, false],
            [1, false],
            [1, false],
            [0, false],
        ],
        [
            [1, false],
            [1, false],
            [0, false],
            [0, false],
        ],
        [
            [1, false],
            [1, false],
            [0, false],
            [0, false],
        ],
        [
            [1, false],
            [1, false],
            [0, false],
            [0, false],
        ]
    ]

    let dapanfills = [
        ['12,1', false],
        ['12,1', false],
        ['12,1', false],
        ['12,1', false],
        ['12,1', false],
        ['12,1', false],
    ]

    function formatNumber(num = 0) {
        console.log(num);
    // Làm tròn số với 2 chữ số thập phân
        if ( num <= 0) {
            return 0;
        } else if (num >= 10) {
            return 10;
        }
        let rounded = Math.round(num * 100) / 100;
        
        // Chuyển số thành chuỗi để kiểm tra phần thập phân
        let str = rounded.toString();
        
        // Nếu chuỗi không có dấu chấm (.) thì thêm ".0" vào
        // if (!str.includes('.')) {
        //     str += '.0';
        // }
        
        // Nếu số thập phân thứ 2 là 0 thì chỉ giữ 1 chữ số phần thập phân
        if (str[str.length - 1] === '0') {
            str = str.slice(0, -1);
        }
        
        return str;
    }

    function countTrueElements(arr = []) {
        let count = 0;
        for (let i = 0; i < arr.length; i++) {
            
            if (arr[i][1] === true) {
                count++;
            }
            
        }
        return count;
    }

    function changeState1in4Answers(index = 0) {
        if (dapan1in4s[index][0] != 0 && index < 12) {
            dapan1in4s[index][1] = !dapan1in4s[index][1];
            mark = mark + ((dapan1in4s[index][1] == true) ? 0.25 : -0.25);
        }
    }

    function changeStateYesNoAnswers(cau = 0, phan = 0) {
        if (dapanyesnos[cau][phan][0] != -1) {
            let last_count = countTrueElements(dapanyesnos[cau])
            dapanyesnos[cau][phan][1] = !dapanyesnos[cau][phan][1]
            let count = countTrueElements(dapanyesnos[cau])
            // console.log(`${last_count} - ${count}`);
            switch (count) {
                case 0:
                    mark = ((last_count < count) ? mark + 0.1 : mark - 0.1)
                    break;
                case 1:
                    mark = ((last_count < count) ? mark + 0.1 : mark - 0.15)
                    break;
                case 2:
                    mark = ((last_count < count) ? mark + 0.15 : mark - 0.25)
                    break;
                case 3:
                    mark = ((last_count < count) ? mark + 0.25 : mark - 0.5)
                    break;
                case 4:
                    mark = ((last_count < count) ? mark + 0.5 : mark - 0.5)
                    break;
                default:
                    // mark = mark + 1.5;
                    break;
            }
        }
    }

    function changeStateFillAnswers(cau = 0) {
        if (dapanfills[cau][0] != '') {
            dapanfills[cau][1] = !dapanfills[cau][1]
            mark = mark + ((dapanfills[cau][1] == true) ? 0.5 : -0.5);
        }
    }
</script>


<div class="">
    <div class="flex flex-col max-w-2xl bg-red-100 p-4 select-none font-inter gap-4">
        <div class="">
            <p class="font-bold mb-2 text-center">Phần thi của bạn</p>

            <div class="flex flex-col items-center mb-5">
                <p class="">Điểm bài thi:</p>
                <p class="text-green-800 text-5xl font-semibold">{formatNumber(mark)}</p>
            </div>

            <p class="font-medium mb-2 text-center text-xs">Chọn vào các câu đúng để tính điểm</p>
        </div>
        <p class="font-bold mb-2">Phần I</p>
        <div class="grid grid-cols-12 gap-2 p-2 py-4 bg-green-100 rounded-2xl">
            {#each dapan1in4s as dapan, index}
                <button class={`px-2 h-[60px] rounded-2xl flex transition-all duration-200 shadow-lg justify-center items-center ${dapan1in4s[index][1] == true ? "bg-green-400 text-white" : "bg-white"}`} on:click={() => {changeState1in4Answers(index)}}>
                    <span>{index + 1}</span>.&nbsp;
                    <span class="font-semibold">
                    {
                        (dapan[0] == 1) ? "A" : (dapan[0] == 2) ? "B": (dapan[0] == 3) ? "C": (dapan[0] == 4) ? "C" : "✖️"   
                    }
                    </span>
                </button>
            {/each}
        </div>

        <p class="font-bold mb-2">Phần II</p>

        <div class="grid grid-cols-4 gap-2">
            {#each dapanyesnos as dapan, i}
                <div class="w-full bg-green-100 p-2 rounded-2xl flex flex-col gap-2">
                    <p class="text-nowrap text-center font-semibold">Câu {i + 1}</p>
                    {#each dapan as key, j}
                        <button class={`flex flex-row py-2 px-2 transition-all duration-200 ${dapanyesnos[i][j][1] ? 'bg-green-400 text-white' : 'bg-white'} rounded-xl shadow-lg`} on:click={() => {changeStateYesNoAnswers(i, j)}}>
                            {['a', 'b', 'c', 'd'][j]}) 
                            <span class="flex flex-row justify-center w-full font-semibold">{['Sai', 'Đúng'][parseInt(key[0])]}</span>
                        </button>
                    {/each}
                </div>                    
            {/each}
        </div>

        <p class="font-bold mb-2">Phần III</p>

        <div class="grid grid-cols-6 gap-2 bg-green-100 p-2 py-4 rounded-2xl">
            {#each dapanfills as dapan, index}
                <button on:click={() => {changeStateFillAnswers(index)}} class={`w-full ${dapan[1] ? 'text-white bg-green-400' : 'bg-white'} p-2 shadow-lg transition-all duration-200 rounded-2xl flex flex-col items-center justify-center gap-2 py-6`}>
                    <p class="text-nowrap text-center font-semibold">Câu {index + 1}</p>
                    <p class="text-center text-2xl font-semibold">{dapan[0]}</p>
                </button> 
            {/each} 
        </div>
        <hr />
        <div class="flex justify-center">
            <!-- <Button>Tính điểm</Button> -->
            <Button on:click={() => (showModal = true)}>Tính điểm</Button>
            <Modal title="Kết quả" bind:open={showModal} autoclose>
            
            <div class="flex flex-col">
                <p class="text-center">Điểm của bạn:</p>
                <p class="text-center font-semibold text-5xl mt-4 text-green-800">9.25</p>
            </div>

            <svelte:fragment slot="footer">
                <Button on:click={() => alert('Handle "success"')}>I accept</Button>
                <Button color="alternative">Decline</Button>
            </svelte:fragment>
            </Modal>
        </div>
    
    </div>
</div>