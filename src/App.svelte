<script>
	import Tailwindcss from './Tailwindcss.svelte';
	let number1 = ""
	let number2 = ""
	$: result = number1+number2
	
</script>

<Tailwindcss />
<main>
<section class="text-gray-600 body-font">
  <div class="container px-5 py-24 mx-auto">
    <div class="flex flex-col text-center w-full mb-12">
      <h1 class="sm:text-3xl text-2xl font-medium title-font mb-4 text-gray-900">Master Cleanse Reliac Heirloom</h1>
      
    </div>
    <div class="flex lg:w-2/3 w-full sm:flex-row flex-col mx-auto px-8 sm:space-x-4 sm:space-y-0 space-y-4 sm:px-0 items-end">
      <div class="relative flex-grow w-full">
        <label for="name1" class="leading-7 text-sm text-gray-600">Número 1</label>
        <input type="number" required id="number1" name="number1" class="w-full bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-transparent focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out"  bind:value={number1}>
      </div>
      <div class="relative flex-grow w-full">
        <label for="name2" class="leading-7 text-sm text-gray-600">Número 2</label>
        <input type="number" required id="number2" name="number2" class="w-full bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-transparent focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out"  bind:value={number2}>
      </div>
      <button class="text-white bg-indigo-500 border-0 py-2 px-8 focus:outline-none hover:bg-indigo-600 rounded text-lg">Calcular</button>
    </div>
		<br/>
		<br/>
		<div>
		  <p class="lg:w-2/3 mx-auto leading-relaxed text-base"> 
			Número 1 : {number1}</p>
			<p class="lg:w-2/3 mx-auto leading-relaxed text-base"> 
			Número 2 : {number2}</p>  
		  <p class="lg:w-2/3 mx-auto leading-relaxed text-base"> 
			<strong> Resultado: {result}</strong></p> 
			
		</div>
  </div>
</section>
	
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
		
		font-size: 3em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style> 
