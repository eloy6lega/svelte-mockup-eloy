<script>
	let tiposCafe = [];
  
	async function cargarTiposCafe() {
	  try {
		const response = await fetch('https://apimocha.com/cafesito/conleche');
		if (!response.ok) {
		  throw new Error('Error al cargar los datos');
		}
  
		const data = await response.json();
		console.log(data);
  
		// Utilizamos directamente la respuesta JSON ya que es un arreglo de objetos
		tiposCafe = data;
	  } catch (error) {
		console.error('Error:', error.message);
	  }
	}
  
	cargarTiposCafe();
  </script>
  
  <main>
	<h1>Listado de Cafés</h1>
  
	{#if tiposCafe.length > 0}
	  <table>
		<thead>
		  <tr>
			<th>ID</th>
			<th>Tipo</th>
			<th>Café</th>
		  </tr>
		</thead>
		<tbody>
		  {#each tiposCafe as { id, tipo, cafe }}
			<tr>
			  <td>{id}</td>
			  <td>{tipo}</td>
			  <td>{cafe}</td>
			</tr>
		  {/each}
		</tbody>
	  </table>
	{:else}
	  <p>Cargando tipos de café...</p>
	{/if}
  </main>
  
  <style>
	main {
	  text-align: center;
	  margin: 2rem;
	}
  
	table {
	  width: 100%;
	  border-collapse: collapse;
	  margin-top: 1rem;
	}
  
	th, td {
	  border: 1px solid #ccc;
	  padding: 0.5rem;
	  text-align: left;
	}
  </style>
  