<script>
  import FormConfig from "../components/FormConfig.svelte";
  import FormPickType from "../components/FormPickType.svelte";
    import ViewTest from "../components/ViewTest.svelte";

  // <a href="https://imgbb.com/"><img src="https://i.ibb.co/tHJvFVJ/dai-hoc-quoc-gia-ha-noi.png" alt="dai-hoc-quoc-gia-ha-noi" border="0"></a>
  // <a href="https://ibb.co/xGq0WGG"><img src="https://i.ibb.co/TRMS6RR/Quoc-Huy-Viet-Nam.png" alt="Quoc-Huy-Viet-Nam" border="0"></a>

  let typeForm = "";
  let doneStep1 = false;
</script>

<div class="flex flex-col gap-4">
  <!-- <FormPickType bind:typeForm /> -->

  <ViewTest />

  <!-- <FormConfig /> -->
</div>

<style lang="postcss">
  :global(html) {
    background-color: theme(colors.gray.100);
  }
</style>
