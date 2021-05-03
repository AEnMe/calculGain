<script>
  let priceBuy = null;
  let priceSell = null;
  let gain;
  $: minimum = priceBuy * 1.01;
  $: if (priceBuy == undefined || priceBuy === 0) {
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
      Buy at <input type="number" bind:value={priceBuy} />
    </p>
    <p>Sell at <input type="number" bind:value={priceSell} /></p>
  </div>
  <div class="result" bp="4 offset-5">
    <div class="minmax">
      <p>Minimum selling at {minimum.toFixed(2)}</p>
    </div>
    <div class="gain">
      <p>gain: {gain > 0 ? "+" : ""}{gain.toFixed(2)}%</p>
    </div>
  </div>
</div>
