<script>
	import {
		Button,
		Table,
		TableBody,
		TableBodyCell,
		TableBodyRow,
		TableHead,
		TableHeadCell
	} from 'flowbite-svelte';

	let times = [];

	let getTrainTimes = async () => {
		const apiKey = 'pDDuZJyKSfzVU1zRriSw4vWvzpRAoGIAtw0osQPqkwn9MOIpOVpGTeEoMM94jXZw';
		const headers = {
			'X-Api-Key': apiKey,
			'Content-Type': 'application/json'
		};

		const response = await fetch('https://ptvapiwrapper.azurewebsites.net/trains/get-all-routes', {
			method: 'GET',
			headers: headers
		})
			.then((response) => response.json())
			.then((data) => {
				times = data;
				console.log(times);
			})
			.catch((err) => {
				console.log(err);
				times = [];
			});
	};
</script>

<Button on:click={getTrainTimes}>Get Train Times</Button>

<Table class="table-fixed">
	<TableHead>
		<TableHeadCell class="max-w-sm">Train Line</TableHeadCell>
		<TableHeadCell>Platform/Time</TableHeadCell>
		<TableHeadCell>Platform/Time</TableHeadCell>
		<TableHeadCell>Platform/Time</TableHeadCell>
	</TableHead>
	<TableBody class="divide-y">
		{#each times as time}
			<TableBodyRow>
				<TableBodyCell class="truncate...">{time.route_name}</TableBodyCell>
				<TableBodyCell>5 mins</TableBodyCell>
				<TableBodyCell>15 mins</TableBodyCell>
				<TableBodyCell>25 mins</TableBodyCell>
			</TableBodyRow>
		{/each}
	</TableBody>
</Table>
