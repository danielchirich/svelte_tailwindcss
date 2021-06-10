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
<div class="h-auto flex items-center justify-center">
<div class="w-full md:w-1/3 bg-white rounded-lg items-center">
<h1 class="text-3xl text-center text-gray-700 mb-4">Todo</h1>

<div class="px-12 pb-10">
{#each todos as todo}
	
		<input
			type=checkbox
			bind:checked={todo.done}
			class="" 
		>
    <div class="w-full mb-2">
       <div class="flex justify-center">
           <input 
		    type=date
		    placeholder="Nuevo Pago Fecha"
		    bind:value={todo.fecha}
		    disabled={todo.done}
            class="px-8 w-full border rounded py-2 text-gray-700 focus:outline-none" />
       </div>
    </div>

	<div class="w-full mb-2">
       <div class="flex justify-center">
           <input 
		    type=text
		    placeholder="Cliente Nombre"
	            bind:value={todo.textClient}
		    disabled={todo.done}
            class="px-8 w-full border rounded py-2 text-gray-700 focus:outline-none" />
       </div>
    </div>
	
	<div class="w-full mb-2">
       <div class="flex justify-center">
           <input 
		    type=number
			placeholder="Pago Cantidad"
			bind:value={todo.numberCantidad}
			disabled={todo.done}
            class="px-8 w-full border rounded py-2 text-gray-700 focus:outline-none" />
       </div>
    </div>    
	
	<div class="w-full mb-2">
       <div class="flex justify-center">
           <input 
		    type=text
			placeholder="Descripción"
			bind:value={todo.textDetalle}
			disabled={todo.done}
            class="px-8 w-full border rounded py-2 text-gray-700 focus:outline-none" />
       </div>
    </div>	
	<div class="w-full mb-2">
       <div class="flex justify-center">
            <input 
		    type=number
			placeholder="Importe"
			bind:value={todo.numberImporte}
			disabled={todo.done}
            class="px-8 w-full border rounded py-2 text-gray-700 focus:outline-none" />
       </div>
    </div>  	
				
{/each}

<button on:click={add} class="w-full mt-6 py-2  rounded bg-blue-500 text-gray-100  focus:outline-none ">
	Agregar Nuevo
</button>

<button on:click={clear} class="w-full mt-6 py-2  rounded bg-blue-500 text-gray-100  focus:outline-none">
	Quitar Pagado
</button>

</div>

{#each todosSort as todoSort,i}
		<ul>
		    <li class="">
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




 
