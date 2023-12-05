<script>
	import TrainTimes from './trainTimes.svelte';
	import Weather from './weather.svelte';
</script>

<div class="grid grid-cols-4 gap-4 max-w-2xl mx-auto shrink">
	<div class="col-span-1">Profile icon</div>
	<div class="col-span-3">
		<Weather />
	</div>
	<div class="col-span-4"><TrainTimes /></div>
</div>
