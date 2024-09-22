<script>
	import { onMount } from 'svelte';
    export let dateUrl;

    let data = [];
    let loading = true;
    let error = null;

    const apiUrl = `http://localhost:3015/api/v1${dateUrl}`;

    onMount(async()=>{
        try {
            const response = await fetch(apiUrl);
            data = await response.json();
        } catch (err) {
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
	<div>
		<ul class="flex flex-wrap justify-between bg-blue-100 p-3 rounded-lg">
			<li class="mr-2">{data.id}</li>
			<li>{data.day}/{data.month}/{data.year}</li>
		</ul>
	</div>
{/if}