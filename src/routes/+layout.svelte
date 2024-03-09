<script lang="ts">
	import 'tailwindcss/tailwind.css';
	import List from '../components/List.svelte';
	type Tarefa = {
		id: number;
		nome: string;
		checked: boolean;
	};

	let tarefa: Tarefa[] = [];
	let value = '';
	$: disableButton = value === '';

	function addTarefa() {
		tarefa = [...tarefa, { id: tarefa.length + 1, nome: value, checked: false }];
		value = '';
	}
</script>

<div class="app pt-10">
	<main class="container">
		<slot />
		<section class="flex flex-col gap-10">
			<form
				class="bg-slate-200 rounded-lg p-5 shadow-md flex gap-5"
				on:submit|preventDefault={addTarefa}
			>
				<input
					bind:value
					type="text"
					placeholder="Digite sua tarefa..."
					class="input input-bordered w-full max-w-xs"
				/>
				<button class="btn" disabled={disableButton}>ADD Tarefa</button>
			</form>
			<List tarefas={tarefa} />
		</section>
	</main>
</div>

<style>
	.app {
		display: flex;
		justify-content: center;
		height: 100vh;
	}
</style>
