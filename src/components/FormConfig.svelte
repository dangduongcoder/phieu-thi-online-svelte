<script>

    import { Fileupload, Label, Helper, Input, Toggle, GradientButton, Select, Button  } from 'flowbite-svelte';

    import { fade, blur } from 'svelte/transition';

    export let type = 'THPTQG 2025';

    let pdfFile = '';
    let isUsePdf = true;
    let testTime = 0;
    let isUseTime = true;
    let typeTestTHPTQG = [
        { value: 'toan', name: 'Toán (12-4-6)' },
        { value: 'lyhoasinhdia', name: 'Lí, Hoá, Sinh, Địa (18-4-6)' },
        { value: 'supl', name: 'Sử, GDKT-PL, Công nghệ (24-4-0)' },
        { value: 'tinhoc', name: 'Tin học (24-6-0)' },
        { value: 'ngoaingu', name: 'Ngoại ngữ (40-0-0)' }
    ];
    let typeSelected;

    export let configs = {
        pdfFile: pdfFile,
    }


</script>

<div class="flex flex-col w-full pt-10">
    <p class="text-center text-2xl">Cấu hình phiếu thi</p>
    <p class="text-center text-xs mt-2">
        Tuỳ chỉnh các thông số của phiếu để phù hợp với nhu cầu của bạn
    </p>
    <div class="container max-w-screen-xl flex flex-col sm:flex-row mx-auto p-2 px-6 pt-10 justify-center gap-4">
        {#if isUsePdf}
            <div in:fade={{ duration: 200 }} out:fade={{ duration: 200 }} class="flex flex-row justify-center transition-all duration-200">
                <div class="flex flex-col items-center">
                    <div class="h-[222px] w-[157px] bg-gray-300 rounded-xl"></div>
                    <p class="text-xs text-red-600 text-center mt-2">Đề thi chưa được tải lên</p>
                    <Fileupload id="with_helper" class="mb-2 mt-2" bind:pdfFile/>
                    <Helper>Vui lòng tải file đề lên ở dạng <span class="font-bold">PDF</span>.</Helper>
                </div>
            </div>
        {/if}

        <div class="grid grid-cols-1 sm:grid-cols-1 md:grid-cols-3 gap-4">
            <div class="flex flex-col gap-4">
                <div>
                    <Label for="test-title" class="mb-2 text-base">Tiêu đề bài làm</Label>
                    <Input type="text" id="test-title" placeholder="VD: Kiểm tra GK Toán" />
                </div>
                <hr/>
                <div>
                    <Label for="" class="mb-2 text-base">Tuỳ chọn PDF</Label>
                    <Toggle bind:checked={isUsePdf}>Sử dụng file đề PDF</Toggle>
                </div>
            </div>

            <div class="flex flex-col gap-4">
                <div>
                    <Label for="test-type" class=" text-base">Lựa chọn môn</Label>
                    <Helper color='green'>Vui lòng lựa chọn đúng bộ môn để phần tính toán điểm thi được chính xác nhất.</Helper>
                    <Select id="test-type" class="mt-2" items={typeTestTHPTQG} bind:value={typeSelected} />

                </div>
            </div>

            <div class="flex flex-col gap-4">
                <div>
                    {#if isUseTime}
                        <Label for="test-time" class="mb-2 text-base">Thời gian làm bài (phút)</Label>
                        <Input type="number" id="test-time" value={testTime == 0 ? '' : testTime} placeholder="VD: 30, 50, 90, 150" />
                        <div class="flex flex-row gap-1 mt-2 flex-wrap ">
                            <GradientButton size="xs" outline pill color="redToYellow" on:click={() => {testTime = 30}}>30 phút</GradientButton>
                            <GradientButton size="xs" outline pill color="cyanToBlue" on:click={() => {testTime = 45}}>45 phút</GradientButton>
                            <GradientButton size="xs" outline pill color="greenToBlue" on:click={() => {testTime = 50}}>50 phút</GradientButton>
                        </div>
                        <div class="flex flex-row gap-1 mt-2 flex-wrap ">
                            <GradientButton size="xs" outline pill color="purpleToPink" on:click={() => {testTime = 60}}>60 phút</GradientButton>
                            <GradientButton size="xs" outline pill color="pinkToOrange" on:click={() => {testTime = 90}}>90 phút</GradientButton>
                            <GradientButton size="xs" outline pill color="tealToLime" on:click={() => {testTime = 120}}>120 phút</GradientButton>
                        </div>
                    {/if}

                    <Toggle class="mt-4" bind:checked={isUseTime}>Sử dụng bộ đếm thời gian</Toggle>
                    
                </div>
            </div>
        </div>
        
    </div>
    <div class="transition-all duration-200 flex justify-center pt-10">
        <Button class="">Tiếp tục</Button>
      </div>
</div>
