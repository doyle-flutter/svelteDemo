<script>
    import {state} from './DrawerState.js';
    import Drawer from './Drawer.svelte';
    var check;
    state.subscribe(v => check = v.check);
</script>
<main class="mainViewStyle">
    Main
    <Drawer />
</main>
<style>
    .mainViewStyle{
        text-align: center;
        height: 100vh;
        color: white;
        padding-top: 5%;
        background-color: red;
    }
</style>