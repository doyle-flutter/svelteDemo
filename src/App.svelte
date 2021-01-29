<script>
	import MainView from './MainView.svelte';
	import ErrorView from './ErrorView.svelte';
	import SearchView from './SearchView.svelte';
	import {state} from './state.js';
	
	var inputData;
	var personData;
	state.subscribe(v => {
		inputData = v.inputData
		personData = v.personData;
	});
</script>

<main>
	{#if personData.length === 0}
		<MainView />
		{:else if personData === 'error'} <ErrorView />
		{:else} <SearchView />
	{/if}
</main>

<style>
	main {
		padding: 0;
		margin: 0;
	}
</style>