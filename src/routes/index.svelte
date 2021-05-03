<script>
  import Buy from "../components/Buy.svelte";
  import Sell from "../components/Sell.svelte";
</script>

<svelte:head>
  <title>Bitcoin Project</title>
</svelte:head>

<Buy />
<hr />
<Sell />

<style>
  :global(.setNumbers) {
    padding: 5px 0;
    margin: auto;
  }

  :global(.result) {
    text-align: center;
    margin: 0px 0px;
    padding: 0px 0px;
  }
</style>
