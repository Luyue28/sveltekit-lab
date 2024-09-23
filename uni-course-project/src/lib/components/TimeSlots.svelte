<script>
	import { timeslotStore } from './../../store.js';
    import { onMount } from "svelte";
    import TimeSlot from "./TimeSlot.svelte";

    let data = [];
	let loading = true;
	let error = null;

    const apiUrl = 'http://localhost:3015/api/v1/timeslots/';

    // 当组件挂载时，发送异步请求
    onMount(async()=>{
        try {
            // first fetch ： { "meta": { "count": 16...}, "data": ["/timeslots/1", "/timeslots/2"...]}
            const response = await fetch(apiUrl);
            const urlArr = await response.json();

            // second fetch ：  [Promise, Promise...]
			const fetchEach = urlArr.data.map(async (url) => {
				const res = await fetch(`http://localhost:3015/api/v1${url}`);
				return res.json();
			});

			// wait for all fetches ： {id: 1, ...duration: 15}，{id: 2, ...duration: 15}...
			data = await Promise.all(fetchEach);
            timeslotStore.set(data);
        } catch(err) {
            error = err.message;
        } finally {
            loading = false;
        }
    });
</script>

{#if loading}
	<p>Loading...</p>
{/if}

{#if error}
	<p>Error: {error}</p>
{/if}

{#if !loading && !error}
	<div class="grid grid-cols-1 gap-4 md:grid-cols-2 lg:grid-cols-4">
		{#each $timeslotStore as item}
			<TimeSlot timeslot={item} />
		{/each}
	</div>
{/if}