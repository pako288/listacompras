<script>
  let arregloTotal = [
    {
      id: crypto.randomUUID(),
      nombre: `Jombe`,
    },
    { id: crypto.randomUUID(), nombre: `Adan` },
    { id: crypto.randomUUID(), nombre: `Jorge` },
  ];


  let inputValue = ``;




  const deleteArray = (id) => {
    arregloTotal = arregloTotal.filter((ele) => ele.id !== id);
  };
  const handleSubmit = (e) => {
    e.preventDefault();
    let todoMap = arregloTotal.map( el => el.nombre)

 if (todoMap.includes(inputValue)) {
    alert("El nombre ya existe");
    inputValue = ``
 return 
 }

   const item = {
      id: crypto.randomUUID(),
      nombre: inputValue
    };

    arregloTotal = [...arregloTotal, item];

    inputValue = ``;
  };
</script>

<form action="" on:submit={handleSubmit}>
  <input
    type="text"
    name=""
    id=""
    placeholder="escribe"
    bind:value={inputValue}
  />
</form>
Element List
{#if arregloTotal.length <= 0}
     <p>The list is empty</p>
     {:else}

<article>

    {#each arregloTotal as elemento}
    <section>
    <p>{elemento.nombre}</p>
    
    <button on:click={deleteArray(elemento.id)}
      >Eliminar {`${elemento.nombre} `}</button
    >
  </section>
    {/each}


</article>
     

{/if}
<style>

  article{
    display: flex;
    width: 100%;
    height: max-content;
    flex-direction: column;
  }

  section{
    font-size: 20px;
    font-weight: 600;
    padding: 4px;
      background: rgb(129, 232, 250);
      display: flex;
      width: 100%;
      flex-wrap: wrap;
      flex-direction: row;
      justify-content: space-between;
      margin-top: 5px;
      text-wrap: pretty;


      & button{
        width: 150px;
        transition: .4s ease-in;
        text-overflow: ellipsis;
        overflow: hidden;
        outline: none;
        border: none;
        max-height: 60px;


        &:hover{
          background: lightcoral;

        }
      }
    }
</style>
