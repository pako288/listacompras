<script>
  let cursos = [`html`, `css`, `js`];
  let paraAgregar = `Jacinto`;

  const handleAdd = () => {
    cursos = [...cursos, paraAgregar];
  };


</script>

<h1>Condicionales y bucles</h1>
{#if cursos.length > 3}
  <h2>Felicidades</h2>
{:else}
  <button class="btn btn-primary" on:click={handleAdd}>Agregar</button>
{/if}
{#each cursos as curso}
  <p>{curso}</p>
{/each}


