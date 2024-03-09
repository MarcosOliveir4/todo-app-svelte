<script lang="ts">
	type Tarefa = {
		id: number;
		nome: string;
		checked: boolean;
	};

	export let tarefas: Tarefa[];

	function removeTarefa(index: number) {
		tarefas.splice(index, 1);
		tarefas = [...tarefas];
	}
</script>

<section class="bg-slate-200 p-5 rounded-lg shadow-md">
	{#if tarefas.length === 0}
		<p class="text-center">Nenhuma tarefa cadastrada</p>
	{/if}
	<ul class="flex flex-col">
		{#each tarefas as { id, nome, checked }, i}
			<li class="flex justify-between">
				<input type="checkbox" class="checkbox checkbox-success" bind:checked />
				<span class="text-lg {checked ? 'line-through' : 'no-underline'}">
					{nome}
				</span>
				<button
					class="btn btn-sm btn-circle btn-outline btn-error"
					on:click={() => removeTarefa(i)}
				>
					<svg
						xmlns="http://www.w3.org/2000/svg"
						class="h-6 w-6"
						fill="none"
						viewBox="0 0 24 24"
						stroke="currentColor"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M6 18L18 6M6 6l12 12"
						/>
					</svg>
				</button>
			</li>
			<span class="divider"></span>
		{/each}
	</ul>
</section>
