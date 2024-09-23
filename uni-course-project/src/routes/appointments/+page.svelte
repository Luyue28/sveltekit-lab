<script>
	import { onMount } from 'svelte';
    export let data;
    import Appointment from '$lib/components/Appointment.svelte';
    import { appointmentStore } from '../../store.js';

    onMount(()=>{
        appointmentStore.set(data.data);
    });
</script>

<section>
    <h2 class="text-center text-2xl">Appointments</h2>
</section>

<section class="items-center text-center flex mt-5">
    <table class="table-auto -collapse w-full">
        <thead>
            <tr>
                <th class="text-lg px-4 py-2"> Date </th>
				<th class="text-lg px-4 py-2"> Timeslot </th>
				<th class="text-lg px-4 py-2"> Name </th>
				<th class="text-lg px-4 py-2"> Breed </th>
				<th class="text-lg px-4 py-2"> State </th>
            </tr>
        </thead>
        <tbody>
            {#each $appointmentStore as item}
            <Appointment appointment = {item}/>
            {/each}
        </tbody>
    </table>
</section>