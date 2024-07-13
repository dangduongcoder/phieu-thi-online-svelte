<script>
    

    import { Badge, Button, Toast } from "flowbite-svelte";
    import { slide, blur } from 'svelte/transition';

    export let typeForm = ""
    export let done = false

    let typeForms = [
        [
            "THPTQG 2025",
            "https://i.ibb.co/TRMS6RR/Quoc-Huy-Viet-Nam.png",
            "open",
        ],
        [
            "DGNL ĐHQGHN",
            "https://i.ibb.co/tHJvFVJ/dai-hoc-quoc-gia-ha-noi.png",
            "coming"
        ],
        [
            "DGNL ĐHBKHN",
            "https://i.ibb.co/7tJWzT9/BachKhoa.png",
            "coming"
        ],
    ]

    let showToast = false

    function triggerToast() {
        showToast = true;
        setTimeout(() => {
            showToast = false;
        }, 3000);
    }


</script>

<div class="fixed right-0 p-4 transition-all duration-200">
    <Toast transition={blur} bind:toastStatus={showToast}>
        Vui lòng chọn mẫu phiếu trước khi tiếp tục !
    </Toast>
</div>

<div class="flex flex-col w-full pt-10">
    
    <p class="text-center text-2xl">Danh sách các mẫu phiếu</p>
    <p class="text-center text-xs mt-2">Chọn một trong các phiếu có sẵn bên dưới và chuyển tiếp sang phần cầu hình</p>
    <div class="container max-w-screen-xl flex-col mx-auto p-2 px-6">
      <div class="flex">
        <div class="grid grid-cols-3 gap-3 mx-auto pt-10">
            {#each typeForms as type}
              <button on:click={() => {if (type[2] != 'coming') typeForm = (typeForm == type[0]) ? "" : type[0] }} class={`px-10 py-8 flex flex-col items-center justify-start rounded-3xl transition-all duration-200 ${(typeForm == type[0] && type[2] != 'coming') ? 'bg-green-400 text-white' : 'bg-white text-gray-500 hover:text-green-600 hover:bg-green-100'}`}>
                <p class="text-2xl font-semibold">{type[0]}</p>
                <img class="h-[120px] mt-6" src={type[1]} alt="" srcset="">
                {#if type[2] == "coming"}
                  <Badge class="mt-4" color="purple">Sắp ra mắt...</Badge>
                {/if}
              </button>
            {/each}
          </div>
      </div>
      <div class="transition-all duration-200 flex justify-center pt-10">
        <Button on:click={() => {if (typeForm != "") {done = true} else {done = false; triggerToast()} }} class="">Tiếp tục</Button>
      </div>
    </div>
</div>