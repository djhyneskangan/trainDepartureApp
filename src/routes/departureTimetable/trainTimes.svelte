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

	let getTrainTimes = async () => {
		const response = await fetch('https://ptvapiwrapper.azurewebsites.net/trains/get-all-routes')
			.then((response) => response.json())
			.then((data) => {
				times = data;
			})
			.catch((err) => {
				console.log(err);
				times = [];
			});
	};
</script>

<Button on:click={getTrainTimes}>Get Train Times</Button>

<Table>
	<TableHead>
		<TableHeadCell>Train Line</TableHeadCell>
		<TableHeadCell>Platform/Time</TableHeadCell>
		<TableHeadCell>Platform/Time</TableHeadCell>
		<TableHeadCell>Platform/Time</TableHeadCell>
	</TableHead>
	<TableBody class="divide-y">
		<TableBodyRow>
			<TableBodyCell>Alameinjjjjjjjjjjjjjjj</TableBodyCell>
			<TableBodyCell>5 mins</TableBodyCell>
			<TableBodyCell>15 mins</TableBodyCell>
			<TableBodyCell>25 mins</TableBodyCell>
		</TableBodyRow>
		<TableBodyRow>
			<TableBodyCell>Cragieburn</TableBodyCell>
			<TableBodyCell>18 mins</TableBodyCell>
			<TableBodyCell>25 mins</TableBodyCell>
			<TableBodyCell>35 mins</TableBodyCell>
		</TableBodyRow>
		<TableBodyRow>
			<TableBodyCell>Frankston</TableBodyCell>
			<TableBodyCell>10 mins</TableBodyCell>
			<TableBodyCell>34 mins</TableBodyCell>
			<TableBodyCell>45 mins</TableBodyCell>
		</TableBodyRow>
	</TableBody>
</Table>
