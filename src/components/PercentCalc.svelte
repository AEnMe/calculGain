<script>
  $: nombre = null;
  $: pourcent = null;

  function per(nombre, pourcent) {
    pourcent /= 100;
    return nombre + nombre * pourcent;
  }
</script>

<p>Gain brut selon pourcentage</p>
<input type="number" bind:value={nombre} min="0" />
<input
  id="pourcentage"
  type="number"
  bind:value={pourcent}
  min="0"
  max="100"
  step="0.05"
/>%
<div>
  <p>
    {Intl.NumberFormat("fr-FR").format(per(nombre, pourcent).toFixed(2))} ({Intl.NumberFormat(
      "fr-FR",
      { signDisplay: "exceptZero" }
    ).format((per(nombre, pourcent) - nombre).toFixed(2))})
  </p>
</div>

<style>
  #pourcentage {
    text-align: center;
    width: 5em;
  }
  input {
    width: 10em;
  }
</style>
