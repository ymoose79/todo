<script>
	import { createEventDispatcher } from 'svelte';
	import Button from './Button.svelte';

	const dispatch = createEventDispatcher();

	export let title;
</script>

<div class="modal-backdrop" on:click>
	<div class="modal">
		<h1>{title}</h1>
		<div class="buttonBox">
			<Button on:click mode="closeMod">Close</Button>
		</div>
	</div>
</div>

<style>
	.modal-backdrop {
		position: fixed;
		margin: auto;
		top: 0;
		left: 0;
		width: 100%;
		height: 100vh;
		background: rgba(0, 0, 0, 0.25);
		z-index: 10;
	}

	.modal {
		position: fixed;
		top: 6vh;
		max-height: 25vh;
		background: white;
		border-radius: 5px;
		z-index: 100;
        box-shadow: 0 4px 6px -1px rgba(57, 31, 91, 0.24), 0 2px 4px -1px #B384C9;
        
	}

	h1 {
		font-size: 2rem;
		text-align: center;
		padding: 1rem;
		margin: 0;
		border-bottom: 1px solid #ccc;
		font-family: 'Roboto Slab', sans-serif;
	}
    .buttonBox{
       display: flex;
        justify-content: center;
        padding-top: .5rem;
        padding-bottom: 1rem;
    }

	@media (min-width: 425px) {
		.modal {
			width: 40rem;
			left: calc(50% - 20rem);
		}
	}
</style>
