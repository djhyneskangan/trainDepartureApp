<script>
	import { onMount } from 'svelte';

	let weatherData = {};

	onMount(async () => {
        const response = await fetch(
            `https://api.openweathermap.org/data/2.5/weather?q=Melbourne,au&appid=655d31f3a94eefed114602aa7f045194`
        );
        weatherData = await response.json();
    });
</script>

<style>
	.weather-info {
		border: 1px solid #000;
		padding: 15px;
		width: 28%;
		margin-left: auto;
		margin-right: 0;
	}
</style>

<div>
	{#if weatherData.main}
		<div class="mb-2 text-2  font-bold  weather-info">
			<h1>{weatherData.name}</h1>
			<h5 class="mb-2 text-3xl font-bold tracking-tight text-gray-900 dark:text-white">{Math.round(weatherData.main.temp - 273.15)}°C</h5>
			<p class="font-normal text-gray-700 dark:text-gray-400 leading-tight">{weatherData.weather[0].description}</p>
		</div>
	{/if}
</div>
