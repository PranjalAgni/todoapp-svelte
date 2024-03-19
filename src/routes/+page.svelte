<script lang="ts">
	import TodoForm from "../components/TodoForm.svelte";
	let todos: { title: string; done: boolean }[] = [];
	function addTodo(todo: string) {
		todos = [
			...todos,
			{
				title: todo,
				done: false
			}
		];
	}

	function removeTodo(id: number) {
		todos.splice(id, 1);
		todos = todos;
	}

	$: console.log("todos", todos);
</script>

<main>
	<TodoForm {addTodo} />
	<span>Total todos: {todos.length}</span>
	<ul>
		{#each todos as todo, index}
			<div>
				<button class="unset" on:click={() => (todo.done = !todo.done)}>
					<li class:done={todo.done}>
						{#if todo.done}
							<span>✅</span>
						{/if}
						<span>{todo.title}</span>
						<button class="unset" on:click={() => removeTodo(index)}>
							<span class="delete">🗑️</span>
						</button>
					</li>
				</button>
			</div>
		{/each}
	</ul>
</main>

<style>
	.done {
		text-decoration: line-through;
	}

	.unset {
		all: unset;
	}

	.delete {
		display: inline-block;
	}

	.delete:hover {
		transform: scale(2);
	}
</style>
