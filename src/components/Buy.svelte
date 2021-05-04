<script>
  export let fees;
  $: fees /= 100;
  let priceBuy = null;
  let priceSell = null;
  let gain;

  $: minimum = priceBuy * (1 + fees * 2);

  $: if (priceBuy == undefined || priceBuy === 0) {
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
      Buy at <input type="number" bind:value={priceBuy} min="0" />
    </p>
    <p>
      Sell at <input type="number" bind:value={priceSell} min="0" />
    </p>
  </div>
  <div class="result" bp="12">
    <div class="minmax">
      <p>
        Minimum selling at {Intl.NumberFormat("fr-FR").format(
          minimum.toFixed(2)
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
