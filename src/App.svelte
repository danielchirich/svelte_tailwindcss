<script>
	import Tailwindcss from './Tailwindcss.svelte';
	
	let todos = [
		{ done: false,
		    fecha: '',
		    textClient: '' ,
			numberCantidad: '',
			textDetalle: '',
			numberImporte: ''  }
		
	];
    

	function add() {
		todos = todos.concat({ done: false,
		                       fecha: '',
							   textClient: '',
							   numberCantidad: '',
							   textDetalle: '',
							   numberImporte: '' });
	}

	function clear() {
		todos = todos.filter(t => !t.done);
	}

	$: byName = todos.slice(0)
      
    $: todosSort = byName.sort(function(a,b) {
       let x = a.textClient.toLowerCase()
       let y = b.textClient.toLowerCase()
          return x < y ? -1 : x > y ? 1 : 0
    })
	
	
</script>

<Tailwindcss />
<main>
<section class="text-gray-600 body-font"></section>
  
<div class="container px-5 py-24 mx-auto flex flex-wrap items-center">
  <div class="lg:w-2/6 md:w-1/2 bg-gray-100 rounded-lg p-8 flex flex-col md:ml-left w-full mt-5 md:mt-0">
	<h1>Detalle</h1>
<br/>
{#each todos as todo}
	<div class="relative flex-grow w-full">
		<input
			type=checkbox
			bind:checked={todo.done}
			
		>
    <br/>
	    <input
		    type=date
			placeholder="Nuevo Pago Fecha"
			bind:value={todo.fecha}
			disabled={todo.done}
			class=" bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-transparent focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out" 
		>
		<input
		    type=text
			placeholder="Cliente Nombre"
			bind:value={todo.textClient}
			disabled={todo.done}
			class=" bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-transparent focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out" 
		>
		<input
		    type=number
			placeholder="Nuevo Pago Cantidad"
			bind:value={todo.numberCantidad}
			disabled={todo.done}
			class=" bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-transparent focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out" 
		>
		<input
		    type=text
			placeholder="Nuevo Pago Detalle"
			bind:value={todo.textDetalle}
			disabled={todo.done}
			class=" bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-transparent focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out" 
		>
		<input
		    type=number
			placeholder="Nuevo Pago Importe "
			bind:value={todo.numberImporte}
			disabled={todo.done}
			class=" bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-transparent focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out" 
		>
	</div>
	
	<br/>
{/each}
<br/>
<button on:click={add} class="text-white bg-indigo-500 border-0 py-2 px-8 focus:outline-none hover:bg-indigo-600 rounded text-lg">
	Agregar Nuevo
</button>
<br/>
<button on:click={clear} class="text-white bg-indigo-500 border-0 py-2 px-8 focus:outline-none hover:bg-indigo-600 rounded text-lg">
	Quitar Pagado
</button>
<br/>
{#each todosSort as todoSort,i}
		<ul>
		  <li class="lg:w-1/3 mb-1 w-1/2">
		                {i+1}) 
		                {todoSort.fecha}
						{todoSort.textClient} 
						{todoSort.numberImporte}

			</li>			
		</ul>
	{/each}
</div>
</div>




</main>

 <style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}
	h1 {
		color: #ff3e00;
		
		font-size: 2em;
		font-weight: 100;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style> 
