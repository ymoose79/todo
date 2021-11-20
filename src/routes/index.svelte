<script>
	let toDo = '';
	let toDoArr = ['get a job', 'mow the yard', 'wash the car', 'grocery'];
	let todoList = [];

	function checkButton() {
		toDoArr = [toDo, ...toDoArr];
		toDo = '';
	}

	function del(todoItems) {
        console.log(todoList);
		toDoArr = toDoArr.filter((value, i) => todoItems.indexOf(i) == -1)
        todoList = []

	}
</script>

<main>
	<form on:submit|preventDefault={checkButton}>
		<label for="name">Things To do:</label>
		<input type="text" bind:value={toDo} />
		<button>Add to list</button>
	</form>
	<form on:submit|preventDefault={del(todoList)}>
		{#each toDoArr as todo, i}
			<ul>
				<input type="checkbox" bind:group={todoList} value={i} />
				<label for="todo">{todo} </label>
			</ul>
		{/each}
		<h1>{toDo}</h1>
		<button>delete item</button>
	</form>
</main>

<style>
	main {
		margin: 5rem 15rem;
		font-size: 2em;
	}
</style>
