<script>
	import { onMount } from 'svelte';
	let data = [];
	let cats = [];
	onMount(async () => {
		const res = await fetch('http://localhost:3010/pets/');
		const urlArr = await res.json();
		const fetchEach = urlArr.map(async (url) => {
			const fetchEachData = await fetch(`http://localhost:3010${url}`);
			return await fetchEachData.json();
		});
		data = await Promise.all(fetchEach);
		cats = data.filter((item) => item.type === 'Cat');
	});
</script>

<div class="grid grid-cols-1 gap-4 md:grid-cols-2 lg:grid-cols-4">
	{#each cats as cat}
		<ul class="bg-blue-200 p-3 lg:p-4 rounded-lg">
			<li>{cat.id}</li>
			<li>{cat.name}</li>
			<li>{cat.type}</li>
		</ul>
	{/each}
</div>
