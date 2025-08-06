<script>
    import CheckThptqg from "./CheckTHPTQG.svelte";



    import FormThptqg from "./FormTHPTQG.svelte";
    import PdfViewer from 'svelte-pdf';
    
    // import PDF from '~/static/sample-unlocked.pdf';
    
</script>



<div class="container mx-auto grid grid-cols-7">

    <!-- <div class="col-span-4"> -->
        <!-- <CheckThptqg /> -->
        <!-- <PdfViewer url={'./sample-unlocked.pdf'} scale='1.2' showButtons={["navigation", "zoom", "print", "rotate", "pageInfo"]}/> -->
    <!-- </div> -->

    <div class="col-span-3 pt-10">
        <FormThptqg />
    </div>
</div>

