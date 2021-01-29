<script>
    
    import {state} from './state.js';
    var inputData;
	var personData;
    state.subscribe(v => {
		inputData = v.inputData
		personData = v.personData;
	});
</script>

<div>
    SearchView
    <ul>
        {#each personData as data}
            <li>{data}</li>
        {/each}
    </ul>
    <div on:click={(e) => state.update((v) => {
        v.inputData = '';
        v.personData = [];
        return v;
    })}>다시</div>
</div>

<style></style>