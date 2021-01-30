<script>
    import {state} from './DrawerState.js';
    var check;
    state.subscribe(v => check = v.check);
    function click(e){
        state.update(v => {
            v.check = !check
            return v;
        });
    }
</script>
<div class:drawerStyleOpen={check == true} class:drawerStyleClose={check == false} class="drawerStyle">
    <p class="drawerStyleBtn" on:click={click}>Drawer</p>
</div>
<style>
    .drawerStyle{
        position: fixed;
        top: 0;
        left: 0;
        height: 100vh;
        padding-top: 5%;
        border: 2px solid black;
        color: white;
        text-align: center;
        background-color: blue;
    }
    .drawerStyleOpen{
        width: 30%;
    }
    .drawerStyleClose{
        width: 10%;
    }
    .drawerStyleBtn{
        cursor: pointer;
        display: inline-block;
    }
</style>