<script>
	import Button from '../UI/Button.svelte';
	import { fade } from 'svelte/transition';


	let toDo = '';
	let toDoArr = ['get a job', 'mow the yard', 'wash the car', 'grocery'];
	let todoList = [];

	function checkButton() {
		if (toDo === ''){
			return
		}
		toDoArr = [toDo, ...toDoArr];
		toDo = '';
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
		<div id="label" >
			<form on:submit|preventDefault={checkButton}>
				<label for="name" />
				<input id="input-field" type="text" bind:value={toDo} placeholder="thing to do" />
			</form>
		</div>
		<div class="button">
			<Button mode="confirm" on:click={checkButton}>Add to list</Button>
		</div>
	</div>
	<div class="container">
	<form on:submit|preventDefault={del(todoList)}>
		{#each toDoArr as todo, i}
			<ul>
				<input type="checkbox" bind:group={todoList} value={i} />
				<label for="todo">{todo} </label>
			</ul>
		{/each}
		<h1>{toDo}</h1>
		<Button mode="delete">Delete checked Items</Button>
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
		border: .125rem solid rgba(179, 132, 201, .84);
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
	#label {
		margin-right: 3rem;
		height: 1rem;
		
	}
</style>
