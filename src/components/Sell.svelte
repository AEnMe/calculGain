<script>
  export let fees;
  $: fees /= 100;
  let priceBuy = null;
  let priceSell = null;
  let gain;

  $: maximum = priceSell * (1 - fees * 2);

  $: if (priceBuy == undefined || priceSell === 0) {
    gain = 0;
  } else {
    gain = (priceSell * (1 - fees)) / priceBuy;
    gain *= 1 - fees;
    gain -= 1;
  }
</script>

<div bp="grid">
  <div class="setNumbers" bp="4 offset-5">
    <p>
      Sell at <input type="number" bind:value={priceSell} min="0" />
    </p>
    <p>
      Buy at <input type="number" bind:value={priceBuy} min="0" />
    </p>
  </div>
  <div class="result" bp="12 ">
    <div class="minmax">
      <p>
        Maximum buying at {Intl.NumberFormat("fr-FR").format(
          maximum.toFixed(2)
        )}
      </p>
    </div>
    <div class="gain">
      <p>
        gain: {Intl.NumberFormat("fr-FR", {
          style: "percent",
          signDisplay: "exceptZero",
          maximumFractionDigits: "2",
        }).format(gain)}
      </p>
    </div>
  </div>
</div>
