<script>
	import Button from '../UI/Button.svelte';
	import { fade, fly } from 'svelte/transition';
	import { flip } from 'svelte/animate';

	let toDo = '';
	let toDoArr = ['get a job', 'mow the yard', 'wash the car', 'grocery'];
	let todoList = [];

	function checkButton() {
		if (toDo === '') {
			return;
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
	<div class="container--input">
		<div id="input-label" transition:fade>
			<form transition:fade on:submit|preventDefault={checkButton}>
				<label for="name" />
				<input id="input-field" type="text" bind:value={toDo} placeholder="thing to do" />
			</form>
		</div>
		<div class="button">
			<Button mode="delete" on:click={checkButton}>Add</Button>
		</div>
	</div>
	<div class="container-delete">
		<div class="delete-left">
			<Button mode="confirm" on:click={del(todoList)}>Delete</Button>
		</div>
		<div class="delete-right">
			{#each toDoArr as todo, i (todo)}
				<ul out:fly={{ x: -200, duration: 2000 }} animate:flip>
					<input type="checkbox" bind:group={todoList} value={i} />
					<label for="todo">{todo} </label>
				</ul>
			{/each}
		</div>
	</div>
</main>

<style>
	main {
		font-size: 2em;
		background-color: rgb(245, 244, 220);
		width: 65vw;
		margin: 0 auto;
		min-height: 55vh;
	}
	#title {
		text-align: center;
		margin: 5rem 5rem 3rem;
		color: rgba(49, 7, 69, 0.84);
		border-bottom: 0.25rem double #f0b01d;
	}
	.container--input {
		margin-bottom: 1rem;
		display: flex;
		justify-content: center;
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
	.container-delete {
		display: grid;
		grid-template-columns: 27vw auto;
	}
	#input-label {
		margin-right: 3rem;
		height: 1rem;
	}
	ul {
		text-align: left;
		padding: 0 2rem;
	}
	.delete-left {
		margin-top: 5rem;
		justify-self: right;
		padding-right: 4rem;
	}

/* ---------------------------------- 4k */
@media (min-width: 2500px) {
  main {
    width: 50vw;
  }
  .container-delete {
		grid-template-columns: 22vw auto;
	}
}

/* ---------------------------------- Tablet =< */
@media (max-width: 768px) {
	#input-field {
		width: 14rem;
	}
}

/* ---------------------------------- small phones */

@media (min-width: 320px) and (max-width: 767px) {
	main {
		width: 100vw;
		height: 100vh;
		padding-top: 2rem;
	}
	#title {
		margin: 1rem 1rem 2rem;
	}
	.container--input {
		flex-direction: column;
		padding-bottom: 1.5rem;
		border-bottom: 0.25rem double rgba(124, 91, 139, 0.84);
	}
	.button {
		align-self: center;
	}
	#input-label{
		align-self: center;
		margin: 0 0 3rem;
	}
	.container-delete {
		display: flex;
		flex-direction: column-reverse;
		justify-content: center;
	}
	.delete-left {
		margin-top: 0;
		align-self: center;
		padding-right: 0;
	}
	
}

</style>
