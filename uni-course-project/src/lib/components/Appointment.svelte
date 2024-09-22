<script>
	import { onMount } from 'svelte';
    export let appointmentUrl;

    let data = [];
	let loading = true;
	let error = null;

    const apiUrl = `http://localhost:3015/api/v1${appointmentUrl}`;

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
    <tr>
    <td class="px-4 py-2"> {data.theDateId} </td>
	<td class="px-4 py-2"> {data.timeslotId} </td>
	<td class="px-4 py-2"> {data.name} </td>
	<td class="px-4 py-2"> {data.breed} </td>
	<td class="px-4 py-2"> {data.state} </td>
    </tr>
{/if}