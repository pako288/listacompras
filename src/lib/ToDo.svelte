<!-- <script>
  let hola;
  let ToDos = [];
  let ToDo = { id: ``, text: ``, estado: false };

  const AddTodo = () => {
    if (!ToDo.text.trim() || ToDo.text.length <= 0) {
      console.log(`texto vacio`);


      return;
    }

    console.log(`texto con algo`);
 
  };


  const RemoveElements = (id) => {
 

    console.log(id)
  }
  
</script> 

<div class="container">
  <h1 class="display-5 my-3">CRUD</h1>

  <form action="" on:submit|preventDefault={AddTodo}>
    <input
      type="text"
      name=""
      id=""
      class=""
      placeholder="Enter para agregar ToDo"
      bind:value={ToDo.text}
    />
  </form>

  {#each ToDos as item}
    <p>{item.text}</p>
    <button on:click={RemoveElements(item.id)}>
      <i class="bi bi-trash"></i>
    </button>

    <p>{item.estado}</p>

  {/each}
</div>
 -->



 <script>

  let checked = false

  let inputValueTwo = ``
  let guardarChecks = [
    {id: crypto.randomUUID(), 
      name: `primero`

    },
    {
      id: crypto.randomUUID(),
      name: `segundo`
    }
    
  ]

  const clasesita = () => 'tachado';
  

  $: console.log(inputValueTwo)

  let inputValue = ``
  let ToDoList = [
    {id: crypto.randomUUID(),
nombre: `Jombe`,

    },
    {id: crypto.randomUUID(),
      nombre: `Adan`,
    }
  ]

const AddToDo = () => {
  const item = {
    id: crypto.randomUUID(),
    nombre: inputValue,
  }

  ToDoList = [...ToDoList, item]
  inputValue = ``
}


const handleRemoveToDo = (id) => {
  ToDoList = ToDoList.filter( el => el.id !== id)
}
if (localStorage.getItem(`ToDo`)) {
  ToDoList = JSON.parse(localStorage.getItem(`ToDo`))
}
$: localStorage.setItem(`ToDo` , JSON.stringify(ToDoList))



const handleSubmit = () => {

  const itemChecks = {
    id: crypto.randomUUID(),
    name : inputValueTwo
  }
  guardarChecks = [...guardarChecks, itemChecks]

  inputValueTwo = ``

  
}


 </script>



<!-- 
<form action="" on:submit|preventDefault={AddToDo}>
  <input type="text" name="" id=""
  placeholder="Enter para agregar ToDo" bind:value={inputValue}
  >
</form>


{#each ToDoList as toDo}
   <p>{toDo.nombre}</p>
   <button on:click={handleRemoveToDo(toDo.id)}>Remove {toDo.nombre}</button>
{/each} -->




<form action="" on:submit|preventDefault={handleSubmit}>

<input type="text" name="" id="" placeholder="Ingrese para la prueba" bind:value={inputValueTwo}>
</form>

{#each guardarChecks as itemChecks}
   <label for={itemChecks.id} >
    <input type="checkbox" id={itemChecks.id}  class={checked ? clasesita : null } checked={checked}>
    {itemChecks.name}
  
  
   </label>
   <p>{itemChecks.checked}</p>
{/each}

