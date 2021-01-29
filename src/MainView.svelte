<script>
    import {state} from './state.js';
    var inputData;
	var personData;
    state.subscribe(v => {
		inputData = v.inputData
		personData = v.personData;
	});
    var search = async () => {
		var _AIRTABLE_KEY = '';
		var _URL = `https://api.airtable.com/v0/appwOWIDaRO0TiSDf/Table%201?api_key=${_AIRTABLE_KEY}`;
		var result = await fetch(_URL)
				.then(res => {
					if(res.status !== 200) throw new Error('NOT 200!')
					return res.json();
				})
				.then(json => json)
				.catch(e => 'error');
            if(result === 'error'){
                state.update(v => {
                    v.personData = result;
                    v.inputData = '';
                    return v;
                });
            }
            else{
                state.update(v => {
                    v.personData = result.records.filter((e,i, arr) => {
                            if(e.fields.Title === v.inputData) return e;
                        }).map((e,i) => e.fields.Title);
                    v.inputData = '';
                    return v;
                });
            }
		return;
	}
	var onKeyDown = (e) => {
		if(e.code === "Enter"){
			if(e.target.value === '') return alert('입력해주세요');
			return search();
		}
	}
	var onChange = (e) => {
        state.update(v => {
            v.inputData = e.target.value;
            v.personData = [];
            return v;
        });
    }
	var onClick = (e) => {
		if(inputData === '') return alert('입력해주세요');
		return search();
	}
</script>

<div>
    <div>
        <p class="mainTitle">이름으로 검색할 수 있습니다</p>
    </div>
    <div>
        <input type="search" name="name" id="name" on:keydown={onKeyDown} on:change={onChange}/>
    </div>
    <div>
        <button on:click={onClick}>검색</button>
    </div>
</div>

<style>
    div > p.mainTitle{
        color: red;
    }
</style>