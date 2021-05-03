<script>
  let priceBuy = null;
  let priceSell = null;
  let gain;
  $: maximum = priceSell * 0.99;
  $: if (priceBuy == undefined || priceSell === 0) {
    gain = 0;
  } else {
    gain = (priceSell * 0.995) / priceBuy;
    gain *= 0.995;
    gain -= 1;
    gain *= 100;
  }
</script>

<div bp="grid">
  <div class="setNumbers" bp="4 offset-5">
    <p>
      Sell at <input type="number" bind:value={priceSell} />
    </p>
    <p>
      Buy at <input type="number" bind:value={priceBuy} />
    </p>
  </div>
  <div class="result" bp="4 offset-5">
    <div class="minmax">
      <p>Maximum buying at {maximum.toFixed(2)}</p>
    </div>
    <div class="gain">
      <p>gain: {gain > 0 ? "+" : ""}{gain.toFixed(2)}%</p>
    </div>
  </div>
</div>
