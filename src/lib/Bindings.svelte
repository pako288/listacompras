<script>
  import ComponenteChequeado from "./ComponenteChequeado.svelte";
  import Criptomonedas from "./Criptomonedas.svelte";

  let texto = ``;
  let numero = 0;

  let rango = 0;
  let check = false;

  $: console.log(rango)
</script>

<div>
  <h1>Bindings</h1>
<label for="uno">
  <input type="checkbox" name="" id="uno" bind:checked={check} />
  Aceptar politicas de la empresa
</label>
  <button disabled={!check}>Enviar</button>

  <h3>checked: {check}</h3>

  {#if check}
  <ComponenteChequeado/>
  {/if}

  <input
    type="range"
    class="rango"
    name=""
    id=""
    min="0"
    max="5" 
    bind:value={rango}
  />

  <p>{rango}</p>

  <input type="text" name="" id="" bind:value={numero} />
  <p>numero : {numero}</p>

  <input type="text" name="" id="" bind:value={texto} />
  <p>texto : {texto}</p>
</div>
<Criptomonedas/>