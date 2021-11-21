<script>
	import Button from '../UI/Button.svelte';


	let uid = 1;

	let description = '';
	let toDoArr = [
		{ uid: uid++, description: 'get a job' },
		{ uid: uid++, description: 'mow the yard' },
		{ uid: uid++, description: 'wash the car' },
		{ uid: uid++, description: 'grocery' }
	];
	let todoList = [];

	function checkButton() {
		if (description === '') {
			return;
		}
		const newTodo = {
			uid: uid++,
			description: description
		}
		toDoArr = [newTodo, ...toDoArr];
		console.log(toDoArr);
		description = '';
	}

	function del(todoItems) {
		console.log(todoList);
		toDoArr = toDoArr.filter((value, i) => todoItems.indexOf(i) == -1);
		todoList = [];
	}
</script>

<main>
	<h1 id="title">Todo List</h1>
	<div class="container">
		<div id="left">
			<form on:submit|preventDefault={checkButton}>
				<label for="name" />
				<input id="input-field" type="text" bind:value={description} placeholder="thing to do" />
			</form>
		</div>
		<div class="right">
			<Button mode="confirm" on:click={checkButton}>Add to list</Button>
		</div>
	</div>
	<div class="container">
		<form on:submit|preventDefault={del(todoList)}>
        {#each toDoArr as todo, i}
            <ul>
                <input type="checkbox" bind:group={todoList} value={i} />
                <label for="todo">{todo.description} </label>
            </ul>
        {/each}
		<h1>{description}</h1>
		<Button mode="delete">Delete items</Button>
	</form>
</div>
</main>

<style>
	main {
		margin: 5rem 15rem;
		font-size: 2em;
	}
	#title {
		text-align: center;
	}
	#input-field {
		width: 15rem;
		border-radius: 1.5rem;
		padding: 1rem;
		width: 18rem;
		border: 0.125rem solid rgba(179, 132, 201, 0.84);
		-webkit-box-shadow: inset 0 0 8px rgba(0, 0, 0, 0.1), 0 0 16px rgba(0, 0, 0, 0.1);
		-moz-box-shadow: inset 0 0 8px rgba(0, 0, 0, 0.1), 0 0 16px rgba(0, 0, 0, 0.1);
		box-shadow: inset 0 0 8px rgba(0, 0, 0, 0.1), 0 0 16px rgba(0, 0, 0, 0.1);
		padding: 15px;
		background: rgba(255, 255, 255, 0.5);
		margin: 0 0 10px 0;
	}
	.container {
		display: flex;
		justify-content: center;
	}
	#left {
		margin-right: 3rem;
		height: 1rem;
	}
</style>
