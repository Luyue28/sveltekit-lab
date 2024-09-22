<script>
	import Example from '$lib/components/Example.svelte';

</script>

<div class="container w-full mx-auto">
    <section class="mt-4">
        <h2 class="text-6xl">
            A<span class="inline-block bg-blue-100 rounded-lg">ppointments&nbsp;</span>
        </h2>
    </section>
    <section class="flex flex-col lg:flex-row mt-5">
        <div class="basis-4/6 bg-gray-100 rounded-lg p-10 lg:mr-8">
            Schedule
        </div>
        <div class="basis-2/6 bg-gray-100 rounded-lg p-10 lg:mr-8">
            Details
        </div>
    </section>
</div>

<div class="container w-full mx-auto">
    <section class="mt-4">
		<h2 class="text-4xl">
			C<span class="inline-block bg-blue-100 rounded-lg">lients&nbsp;</span>
		</h2>
	</section>
    <section class="flex flex-col lg:flex-row mt-5">
        <div class="basis-4/6 bg-gray-100 rounded-lg p-10 lg:mr-8">
            All my clients
        </div>
    </section>
</div>

<style>
</style>
