<script>
    export let timeslot, appointment;
</script>

<div>
    <ul class="flex w-full">
        {#if !appointment}
			<li class="bg-blue-200 p-3">{timeslot.starttime}</li>
			<li class="bg-blue-100 p-3">---</li>
		{/if}
		{#if appointment}
			<li class="bg-orange-200 p-3">{timeslot.starttime}</li>
			<li class="bg-orange-100 p-3">{appointment.name}</li>
		{/if}
    </ul>
</div>