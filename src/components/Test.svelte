<script>
  let gainSell;
  let gainBuy;
  $: priceBuy = null;
  $: priceSell = null;

  $: priceBuy = null;
  $: priceSell = null;

  $: priceUp = priceBuy * 1.01;
  $: priceDown = priceSell * 0.99;

  $: if (priceBuy == undefined) {
    gainSell = 0;
  } else {
    gainSell = (priceSell * 0.995) / priceBuy;
    gainSell *= 0.995;
    gainSell -= 1; //gain
    gainSell *= 100; //%
  }

  $: if (priceSell == undefined) {
    gainBuy = 0;
  } else {
    gainBuy = (priceBuy * 0.995) / priceSell;
    gainBuy *= 0.995;
    gainBuy -= 1; //gain
    gainBuy *= 100; //%
  }
</script>

<div>
  <h1>Buying</h1>
  <p>
    buy at <input type="number" name="buy" id="" bind:value={priceBuy} />
    sell at <input type="number" name="sell" id="" bind:value={priceSell} />
  </p>
  <p>
    minimum selling at {priceUp.toFixed(2)} (+1%)
  </p>
  <p>
    Gain Sell: {gainSell > 0 ? "+" : ""}{gainSell.toFixed(2)}%
  </p>
</div>

<div>
  <h1>Selling</h1>
  <p>
    buy at <input type="number" name="buy" id="" bind:value={priceBuy} />
    sell at <input type="number" name="sell" id="" bind:value={priceSell} />
  </p>

  <p>maximum buying at {priceDown.toFixed(2)} (-1%)</p>
  <p>Gain Buy: {gainBuy > 0 ? "+" : ""}{gainBuy.toFixed(2)}%</p>
</div>

<style>
  div {
    width: 500px;
    border: solid 1px black;
    margin: 40px 40px;
    padding: 5px 5px;
  }
</style>
