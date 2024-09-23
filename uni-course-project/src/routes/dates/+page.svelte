<script>
	import { onMount } from 'svelte';
    export let data;
    import Date from '$lib/components/Date.svelte';
	import { dateStore } from '../../store.js';

    onMount(()=>{
        dateStore.set(data.data);
    });
</script>

<section>
    <h2  class="text-center text-2xl">Dates</h2>
</section>

<section>
    <div class="grid grid-cols-1 gap-4 md:grid-cols-2 lg:grid-cols-4">
        {#each $dateStore as item}
        <Date date = {item}/>
        {/each}
    </div>
</section>