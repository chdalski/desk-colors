<script lang="ts">
  import { generate } from "@ant-design/colors";
  let colorName: string = "blue";
  let colorHex: string = "#1890ff";
  let genColors = generate(colorHex);
  const createTable = (color: string) => {
    genColors = generate(color);
  };
  const colorToClipboard = async (color: string) => {
    await navigator.clipboard.writeText(color);
  };
</script>

<h1>Color Table</h1>
<input bind:value={colorName} />
<input
  type="color"
  bind:value={colorHex}
  on:change={() => createTable(colorHex)}
/>
<br />
<table>
  {#each genColors as color, i}
    <tr on:click={async () => await colorToClipboard(color)}>
      <td style="color: #000000; background-color:{color}">
        {colorName}-{i + 1}<br />{color}
      </td>
    </tr>
  {/each}
</table>

<style>
  table {
    border-spacing: 0px;
    width: 100%;
  }
  tr {
    height: 20px;
  }
  td {
    text-align: center;
  }
</style>
