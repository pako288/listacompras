<script>
  let inputValue = ``;

  let arrResultado = [];

  let objetoAdd = [];

  if (localStorage.getItem(`arr`)) {
    arrResultado = JSON.parse(localStorage.getItem(`arr`));
  }
  if (localStorage.getItem(`check`)) {
    objetoAdd = JSON.parse(localStorage.getItem(`check`));
  }

  $: localStorage.setItem(`arr`, JSON.stringify(arrResultado));

  $: localStorage.setItem(`check`, JSON.stringify(objetoAdd));

  const handleSubmit = () => {
    if (inputValue.length <= 0) return;
    const newValue = {
      name: inputValue.toUpperCase(),
      id: crypto.randomUUID(),
    };

    const exists = objetoAdd.some((item) => item.name === newValue.name);
    if (!exists) {
      objetoAdd = [...objetoAdd, newValue];
    } else {
      console.log("El articulo ya esta agregado");
    }

    inputValue = ``;
  };

  const RemoveElements = () => {
    objetoAdd = [];
    arrResultado = [];
  }; 
</script>

<h1 style="text-align: center; margin-top: 20px;">Lista de compras</h1>

<form action="" on:submit|preventDefault={handleSubmit}>
  <input
    type="text"
    name=""
    id=""
    class="inpo"
    bind:value={inputValue}
    width="100"
    height="200"
    placeholder="Agregar a la lista"
  />

  <button class="btn btn-primary add">Agregar</button>
</form>

{#if objetoAdd.some((item) => item.name === inputValue.toUpperCase())}
  <p style="color: red;">
    El articulo {inputValue.toUpperCase()} ya esta agregado
  </p>
{/if}

<article>
  <section>
    {#each objetoAdd as item}
      <label
        for={item.id}
        class={arrResultado.includes(item.name) ? "strikethrough" : ""}
      >
        <input
          class="chk a"
          type="checkbox"
          name=""
          id={item.id}
          value={item.name}
          bind:group={arrResultado}
        />{item.name}
      </label>
    {/each}
  </section>
</article>

<button on:click={RemoveElements} class="btn btn-danger remove">
  Limpiar lista</button
>

<style>
  article {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
  }

  section {
    display: flex;
    flex-direction: column;
    padding: 5px;
    gap: 20px;
  }
  .strikethrough {
    text-decoration: line-through;
  }
  .btn {
    margin-left: 5px;
  }

  .remove {
    margin-top: 40px;
  }

  .inpo {
    margin-top: 10px;
    margin: 5px;
    border-radius: 10px;
    background: lightcyan;
    outline: none;
    border: none;
    color: black;
  }

  .inpo:focus {
    color: black;
    font-weight: 600;
    letter-spacing: 0.3px;
  }

  .add {
    transition: 0.6s ease;
  }
  .add:hover {
    background: #1fb43f;
  }

  form {
    bottom: red;
    display: grid;
    grid-template-columns: repeat(1, 70% 1fr);
  }
</style>
