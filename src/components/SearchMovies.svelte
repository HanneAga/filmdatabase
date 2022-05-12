<script>
	let inputValue = '';
	let active = false;
	import { goto } from '$app/navigation';
	import { fly } from 'svelte/transition';

	function cancelInactive() {
		if (inputValue) {
			active = true;
		} else {
			active = false;
		}
	}
	function submitSearch() {
		goto('/search/' + inputValue);
	}
</script>

<form on:submit|preventDefault={submitSearch} class="search">
	{#if !active}
		<label in:fly={{ y: -10, duration: 500 }} out:fly={{ y: -10, duration: 500 }} for="search_movie"
			>Search Movie
		</label>
	{/if}
	<input
		on:blur={cancelInactive}
		on:focus={() => (active = true)}
		bind:value={inputValue}
		name="search_movie"
		type="text"
		class={active ? 'selected' : ''}
	/>
	{#if inputValue}
		<button in:fly={{ x: 0, duration: 500 }} out:fly={{ x: 20, duration: 500 }}>Search</button>
	{/if}
</form>

<style>
	.search {
		position: relative;
		left: 50%;
		top: 0%;
		transform: translate(-50%, -0%);
		width: 30%;
		margin: 3rem 50vh 4rem 0vh;
	}
	button {
		font-size: 00.7rem;
		padding: 0rem 1rem;

		background: #45494e;
		color: white;
		font-weight: bold;
		border: none;
		position: absolute;
		bottom: 50%;
		right: 0;
		transform: translate(0, 50%);
		height: 100%;
		border-top-right-radius: 10px;
		border-bottom-right-radius: 10px;
		cursor: pointer;
	}
	input {
		width: 100%;
		border: none;
		font-size: 1rem;
		font-family: 'Poppins', sans-serif;
		outline: none;
		color: rgb(3, 3, 3);
		padding: 0.5rem 0.1rem;
		transition: background 0.75s ease-out;
		font-weight: bold;
		background: rgb(251, 250, 250);
		border-radius: 10px;
		padding: 1rem;
	}
	label {
		position: absolute;
		font-size: 0.8rem;
		top: 50%;
		left: 0%;
		transform: translate(0, -50%);
		pointer-events: none;
		color: rgb(13, 13, 13);
		padding: 0rem 1rem;
	}
	input.selected {
		background: rgb(250, 249, 249);
	}
</style>
