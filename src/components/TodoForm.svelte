<script lang="ts">
	export let addTodo: (todo: string) => void;
	let newTodo = "";
	function handleSubmit() {
		addTodo(newTodo);
		newTodo = "";
	}
</script>

<form on:submit|preventDefault={handleSubmit}>
	<label>
		New Todo
		<input bind:value={newTodo} placeholder="Enter a todo " />
	</label>
	<button class="container mw-100">Add todo</button>
</form>

<style>
	.mw-100 {
		max-width: 100%;
	}
</style>
