<script>
  let count = 1

  $:doble = 1 
  const increment = () => {
    count += 1
  }

  const duplicarValor = () => {
doble= doble * 2

 


  }
  
</script>

<button on:click={increment}>
  count is {count}
</button>

<button on:click={() => count = 1}>Reiniciar contador </button>


<h2>{doble}</h2>
<button on:click={duplicarValor}>click para duplicar su valor</button>
<button on:click={() => doble = 1}>Reiniciar valor</button>