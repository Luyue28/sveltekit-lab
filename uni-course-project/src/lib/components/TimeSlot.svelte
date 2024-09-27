<script>
    export let contents;
</script>

<div>
  {#if contents.appointment}
			<li class="bg-orange-200 p-3">{contents.starttime}</li>
			<li class="bg-orange-100 p-3">{contents.appointment.name}</li>
      <li class="bg-orange-100 p-3">{contents.appointment.breed}</li>
		{/if} 
    {#if !contents.appointment}
			<li class="bg-blue-200 p-3">{contents.starttime}</li>
			<li class="bg-blue-100 p-3">No appointment</li>
		{/if}
</div>
