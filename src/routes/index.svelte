<script>
  import Buy from "../components/Buy.svelte";
  import Sell from "../components/Sell.svelte";
  import PercentCalc from "../components/PercentCalc.svelte";
  $: myfees = 0.5;
</script>

<svelte:head>
  <title>Bitcoin Project</title>
</svelte:head>

<div class="box">
  <div bp="grid">
    <div class="setNumbers" bp="4 offset-5">
      <p>
        fees: <input
          type="number"
          min="0"
          max="100"
          bind:value={myfees}
          class="fees"
          step="0.05"
        />%
      </p>
    </div>
  </div>
  <hr />
  <Buy fees={myfees} />
  <hr />
  <Sell fees={myfees} />
</div>
<div id="per">
  <PercentCalc />
</div>

<style>
  :global(p) {
    font-family: "Courier New", Courier, monospace;
  }
  hr {
    color: #ccc;
    width: 50%;
  }
  .box,
  #per {
    width: 600px;
    border: 1px solid #ccc;
    border-bottom: 3px solid #ccc;
    border-right: 3px solid #ccc;
    margin: 20px auto;
    padding: 10px;
  }
  :global(div) {
    text-align: center;
  }
  .fees {
    width: 5em;
    text-align: center;
    border: none;
  }
  :global(input) {
    font-family: "Courier New", Courier, monospace;
    background-color: #eee;
    padding: 0 0.5em;
    border: none;
  }

  :global(.result) {
    text-align: center;
    margin: 0px 0px;
  }
</style>
