<script>
    import {state} from './state.js';
</script>
<div>
    <div>오류 페이지</div>
    <div on:click={(e) => state.update((v) => {
        v.inputData = '';
        v.personData = [];
        return v;
    })}>메인화면으로</div>
</div>
<style>

</style>