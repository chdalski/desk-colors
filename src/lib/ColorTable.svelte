<script lang="ts">
  import { generate } from "@ant-design/colors";
  export let colorName: string;
  export let colorHex: string;
  const copyToClipboard = async (color: string) => {
    await navigator.clipboard.writeText(color);
  };
</script>

<table>
  {#each generate(colorHex) as color, i}
    <tr on:click={async () => await copyToClipboard(color)}>
      <td
        style="color: {i < 5 ? '#000000' : '#ffffff'}; background-color:{color}"
      >
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
