<script lang="ts">
  import ColorTable from "./ColorTable.svelte";
  $: colorName = "blue";
  $: colorHex = "#1890ff";
</script>

<h1>Color Calculator</h1>
<input bind:value={colorName} />
<input type="color" bind:value={colorHex} />
<br />
<ColorTable {colorName} {colorHex} />

<style>
</style>
