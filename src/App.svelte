<script>
	import Todo from './components/Todo.svelte';

	let description;
	let addButtonText = 'Add todo';
	let todos = [];

	function keyDown(e) {
		if (e.key === 'Enter') {
    	addTodo();
		}
	}
	
	function addTodo() {
		const id = todos.length;
		const newTodo = { id, text: description, completed: false };
		todos = [...todos, newTodo];
		description = '';
	}
</script>

<main>
	<div class="contents">
		<div class="header">
				stuff to do
		</div>
		<div class="add-container">
				<input type="text" id="txtTodo" on:keydown={keyDown} placeholder="what do you need to do?" bind:value={description} />
				<input type="button" id="btnAdd" class="btn" on:click={addTodo} value={addButtonText} disabled={!description} />
		</div>
		<div class="todo-list">
			{#each todos as todo}
				<Todo todo={todo} />
				<br/>
			{/each}
		</div>
		<!-- <ConfirmBtn buttonText="Clear all your todos?" action={this.clearAll} /> -->
	</div>
</main>

<style>
	main {
		background-color: #282c34;
		color: white;
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
		height: 100%;
		width: 100%;
	}

	.contents {
		margin-top: 300px;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

	.btn {
    border-radius: 5px;
    border: 0px;
	}

	.header {
			display: inline-flex;
	}

	.add-container input {
			margin: 5px;
			border-radius: 5px;
			border: 0px;
			padding: 5px;
	}

	.todo-list {
		display: inline-block;
	}
</style>