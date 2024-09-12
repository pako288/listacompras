<script>

let valueInput = ``
let palabras = ``
let nodos = false

const getValueInput = ({target}) => {
  valueInput = target.value

//   console.log(valueInput)

  palabras = valueInput.trim().split(" ")



  console.log(palabras)
}

const handleSubmit = (e) => {
  e.preventDefault()

  nodos = true


  valueInput= ``
//   nodos = false

}

</script>





<form action="" on:submit={handleSubmit} >

    <input type="text" name="" id="" bind:value={valueInput} on:change={getValueInput} placeholder="Escribe para saber cuantas palabras tiene">
</form>


{#if nodos}
     <p>La frase ingresada tiene {palabras.length} palabras</p>

{/if}