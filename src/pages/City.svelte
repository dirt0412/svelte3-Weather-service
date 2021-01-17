<script>
	import { onMount, onDestroy, beforeUpdate, afterUpdate } from "svelte";

	let data = {};
	let temp = '';
	export let nameCity = '';
	let coord = {lon:'',lat:''};//wspolrzedne
	let humidity = '';//wilgotnosc
	let pressure = '';//cisnienie

	onMount(async () => {
		const res = await fetch(
			`${__myapp.env.API_URL}${nameCity}&appid=${__myapp.env.API_CLIENT_KEY}`
		);
		data = await res.json();
		//console.log(data);
		nameCity = data.name;
		temp = convertToCelsius(data.main.temp);
		coord.lon = data.coord.lon;
		coord.lat = data.coord.lat;
		humidity = data.main.humidity;
		pressure = data.main.pressure;
	});
	beforeUpdate(() => {
		//autoscroll = div && (div.offsetHeight + div.scrollTop) > (div.scrollHeight - 20);
	});

	afterUpdate(() => {
		//if (autoscroll) div.scrollTo(0, div.scrollHeight);
	});
	onDestroy(() => {
		//clearInterval(interval);
	});
	function convertToCelsius(f){
		return (Number((Number(f) - 32)/1.8000)).toFixed(2);
	}
</script>

<h1>{nameCity}  - coord: {coord.lon} , {coord.lat}</h1>
<div>
	<label>temperature</label>
	<input value={temp}>
</div>
<div>
	<label>humidity</label>
	<input value={humidity}>
</div>
<div>
	<label>pressure</label>
	<input value={pressure}>
</div>

