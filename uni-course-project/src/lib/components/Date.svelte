<script>
    export let date;
</script>

<div>
	<ul class="flex flex-wrap justify-between bg-blue-100 p-3 rounded-lg">
		<li class="mr-2">{date.id}</li>
		<li>{date.day}/{date.month}/{date.year}</li>
	</ul>
</div>